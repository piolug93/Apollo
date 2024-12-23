#FROM itsafeaturemythic/mythic_python_dotnet:latest
FROM mcr.microsoft.com/dotnet/sdk:8.0
RUN apt-get update && apt-get install python3 python3-pip python3.11-venv -y

#RUN curl -L -o /donut https://github.com/piolug93/donut/releases/download/2.0.0/donut.exe

WORKDIR /Mythic/
RUN python3 -m venv /venv
RUN /venv/bin/python -m pip install mythic-container==0.5.14
RUN /venv/bin/python -m pip install git+https://github.com/piolug93/donut
RUN /venv/bin/python -m pip install mslex

COPY [".", "."]

# fetch all dependencies
RUN cd apollo/agent_code && dotnet restore

#CMD ["bash", "-c", "cp /donut apollo/agent_code/donut && /venv/bin/python main.py"]
CMD ["bash", "-c", "/venv/bin/python main.py"]
