# Using python 3.12.7 slim image as the base image
FROM python:3.12.7-slim
# Defining working directory and copy the requirements file. We will run the commands inside this new directory
WORKDIR /usr/src/myapp
# Copy requirements.txt  to the working directory
COPY requirements_prod.txt .

# This is for a security issue 
RUN python3 -m pip install "pip @ https://files.pythonhosted.org/packages/3f/06/3e4420302363fbb71be3c7f35ce042f54bfca330e3e66b3a2e3c4cca579f/pip-26.2.2-py3-none-any.whl#sha256=fd7f4dfa8190e014013b9f08f3e973f4e4c26ffd179a204895533a7254813a70"

# Install required python packages
RUN pip install --no-cache-dir -r requirements_prod.txt
# Copy all files in prediction-api local host directory to /usr/src/myapp in Docker container
COPY . .
ENV MODEL_NAME=model.pkl
# Expose the port that our app runs in
EXPOSE 5000
# Run our App
CMD ["python3","app.py"]