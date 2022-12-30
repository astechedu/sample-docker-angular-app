# Dockerized Angular



#Use official node image as the base image

	FROM node:latest as build

#Set the working directory

	WORKDIR /usr/local/app

#Add the source code to app

	COPY ./ /usr/local/app/

#Install all the dependencies

	RUN npm install

#Generate the build of the application

	RUN npm run build


#Stage 2: Serve app with nginx server

#Use official nginx image as the base image

	FROM nginx:latest

#Copy the build output to replace the default nginx contents.

	COPY --from=build /usr/local/app/dist/dockerangular01 /usr/share/nginx/html

#Expose port 80

	EXPOSE 80
	Footer







----- X -----




#Building image

	docker build . -t dockerized_angular

#Running container

	docker run --name angular-app -p 8080:80 -d dockerized_angular

#On Browser

	http://localhost:8080

# Angular


This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 15.0.4.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.
