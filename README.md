# CAP-project
SAP CAP project, Postgres DB, OData, Logging service, AuditLog, Xsuaa, Multi-tenant app, saas-registry

# Requirements:
1. instal node.js https://nodejs.org/
2. Install CAP's cds-dk
> npm add -g @sap/cds-dk


Initialize CAP project 
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
- (in VS Code simply choose _**Terminal** > Run Task > cds watch_)
- Start adding content, for example, a [db/schema.cds](db/schema.cds).


## Learn More

Learn more at https://cap.cloud.sap/docs/get-started/.


Useful commands:
> cds srv/cat-service.cds -2 edmx
> cds db/schema.cds -2 json
> cds db/schema.cds -2 yml
> cds db/schema.cds -2 sql
> cds db/schema.cds //CSN
> cds add hana,approuter,xsuaa --for production