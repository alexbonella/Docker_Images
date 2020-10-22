FROM ubuntu:18.04 

# streamlit-specific commands
RUN mkdir -p /root/.streamlit
RUN bash -c 'echo -e "\
[general]\n\
email = \"\"\n\
" > /root/.streamlit/credentials.toml'
RUN bash -c 'echo -e "\
[server]\n\
enableCORS = false\n\
" > /root/.streamlit/config.toml'

LABEL maintainer "Alexander Bolaño  <alexbonella2806@gmail.com>"
# If you have any comment : LinkedIn - https://www.linkedin.com/in/alexanderbolano/

# Expose port 
EXPOSE 8501

# --------------- Export envirennement variable ---------------
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

RUN mkdir Counting_app 
WORKDIR /Counting_app

RUN apt-get update 
RUN apt install -y python3-pip
RUN apt install -y build-essential libssl-dev libffi-dev python3-dev
RUN apt-get install -y libsm6 libxext6 libxrender-dev
RUN apt install -y libgl1-mesa-glx

COPY . /Counting_app

RUN pip3 install --upgrade pip 
RUN pip3 install --no-cache-dir -r requirements.txt

# Ejecutamos nuestro Script
CMD ["streamlit", "run","--server.port", "8501", "app.py","--server.enableCORS","false"]

