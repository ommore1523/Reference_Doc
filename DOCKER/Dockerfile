

# Base Image Name 
FROM ubuntu:18.04  
LABEL Name="omakr more"
LABEL Email="ommore52326@gmail.com"
RUN cd /tmp/
RUN touch om.txt
ENV Name=omakr
ENV Pass=ommore52326
# RUN useradd $Name  && echo "$Name:$Pass" | chpasswd   --> create username passwd    
# USER $Name  ==> login as omkar user
WORKDIR /var/www/html/   
COPY curr_path_file  /var/www/html/
ADD  curr_path_file  /var/www/html/
CMD ['tree']
EXPOSE 22 