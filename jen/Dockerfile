FROM centos:7
WORKDIR /devops
COPY . .
RUN yum update -y
RUN yum install python3 -y
RUN yum install git -y
RUN git init
RUN git pull https://github.com/irakholla/project.git
RUN cat nginx.repo > /etc/yum.repos.d/nginx.repo
RUN yum install nginx -y
RUN cat nginx.conf > /etc/nginx/nginx.conf
RUN ["chmod", "+x", "/devops/web.sh"]
EXPOSE 5000:5001
ENTRYPOINT ["/devops/web.sh"]
