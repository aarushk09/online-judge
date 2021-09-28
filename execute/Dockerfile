FROM public.ecr.aws/lambda/nodejs:14

RUN yum install -y gcc-c++ amazon-linux-extras zip unzip
RUN amazon-linux-extras install java-openjdk11
RUN amazon-linux-extras enable python3.8
RUN yum install -y python3.8

COPY package.json package-lock.json ./

RUN npm install

COPY tsconfig.json ./
COPY src ./src

RUN npm run build

# Command can be overwritten by providing a different command in the template directly.
CMD ["dist/app.lambdaHandler"]