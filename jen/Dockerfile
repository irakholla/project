FROM centos:7
WORKDIR /devops
COPY nginx.conf /devops/nginx.conf
COPY my_password.txt /devops/my_password.txt
COPY nginx.repo  /devops/nginx.repo
COPY pipeline.sh /devops/pipeline.sh
COPY ps.sh /devops/ps.sh
COPY web.sh /devops/web.sh
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
