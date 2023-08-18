# CAP-project
SAP CAP project, Postgres DB, OData, Logging service, AuditLog, Xsuaa, Multi-tenant app, saas-registry

https://medium.com/nerd-for-tech/sap-tutorial-complete-cap-java-part-1-fc1868c7bbba

# Requirements:
1. instal node.js https://nodejs.org/
2. Install CAP's cds-dk
> npm add -g @sap/cds-dk


Initialize CAP project:
> cds init
> cds add tiny-sample
> npm install
Run application 
> cds watch

# Getting Started
It contains these folders and files, following our recommended project layout:

| File or Folder | Purpose                              |
|----------------|--------------------------------------|
| `app/`         | content for UI frontends goes here   |
| `db/`          | your domain models and data go here  |
| `srv/`         | your service models and code go here |
| `package.json` | project metadata and configuration   |
| `readme.md`    | this getting started guide           |

## Next Steps

- Open a new terminal and run `cds watch`


https://cap.cloud.sap/docs/get-started/
https://medium.com/nerd-for-tech/sap-tutorial-complete-cap-java-part-1-fc1868c7bbba


Useful commands:
> cds srv/cat-service.cds -2 edmx  
> cds db/schema.cds -2 json  
> cds db/schema.cds -2 yml  
> cds db/schema.cds -2 sql  
> cds db/schema.cds //CSN  
> cds add hana,approuter,xsuaa --for production  
> cds srv/cat-service.cds -2 edmx //Compiling APIs, EDMX = Entity Data Model XML  
> cds add mta

### Deploying Persistent Databases
> npm add sqlite3 -D  
> cds deploy --to sqlite:my.sqlite  
> or  
> cds deploy --to hana  

### [Cloud MTA Build Tool](https://sap.github.io/cloud-mta-build-tool/download/)
[Tutorial: Deploy Your Multi-Target Application (MTA)](https://developers.sap.com/tutorials/btp-app-cap-mta-deployment.html)
1. Install MBT [Documentation: Cloud MTA Build Tool](https://sap.github.io/cloud-mta-build-tool)  
>npm install -g mbt  

2. The MultiApps plugin is required to deploy an MTA archive. It needs to be available in your Cloud Foundry landscape’s Cloud Foundry plugin repository.  
> cf install-plugin multiapps   

3. Generate mta.yaml file
> cds add mta

For trial acount you need to change the configuration for hana in mta.yaml:
```angular2html
  - name: hana_db
    type: com.sap.xs.hdi-container
    parameters:
      service: hana-cloud-trial
      service-plan: hana
```

4. Update NPM dependencies. NPM uses a file called package-lock.json to remember which actual version of package was installed and later installs these exact versions and ignores any updates in minor releases not explicitly specified in the package.json file. Maintaining this is important for production applications for consistency. For the purposes of this tutorial, use the latest versions of the packages. To ensure this, delete your older package-lock.json and run npm install --package-lock-only to generate it again to avoid errors due to use of older versions.    
> npm install --package-lock-only 

5. Install GNU Make (Run cmd as administrator and install)   
GNU Make is a tool which controls the generation of executables and other non-source files of a program from the program's source files. Make gets its knowledge of how to build your program from a file called the makefile, which lists each of the non-source files and how to compute it from other files. When you write a program, you should write a makefile for it, so that it is possible to use Make to build and install the program
>choco install make
>choco upgrade make

6. Build mtar file:
> mbt build -t ./

7. Deploy mtar file to Cloud Foundry:
> cf deploy CAP-project_1.0.0.mtar
