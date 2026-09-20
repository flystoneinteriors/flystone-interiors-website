# Flystone Interiors — Fresh Azure Static Web Apps Build

This version is deliberately simple and is configured to avoid the frontend Oryx build error you encountered.

## Azure/GitHub build settings
The included workflow uses:
- app_location: `/`
- api_location: `/api`
- output_location: `''`
- skip_app_build: `true`

Do not add `github_id_token` to the workflow.

## Static Web App setup
Create the Static Web App with **Custom** build preset and connect your GitHub repository. The workflow in `.github/workflows/azure-static-web-apps.yml` is the source of truth for deployment settings.

## Required GitHub secret
The Azure-created deployment workflow normally supplies `AZURE_STATIC_WEB_APPS_API_TOKEN`. Keep this as a repository secret. Do not hard-code it.

## API runtime
`staticwebapp.config.json` sets `apiRuntime` to Node.js 22, which is currently a supported managed-functions runtime for Azure Static Web Apps.

## Azure resources needed later
- Static Web App
- Storage Account for Table Storage + Blob Storage
- SMTP mailbox such as `info@flystoneinteriors.com`

Add API application settings in Azure:
`AzureWebJobsStorage`, `PROJECTS_TABLE`, `ENQUIRIES_TABLE`, `BLOB_CONTAINER`, `ADMIN_EMAILS`, `SMTP_HOST`, `SMTP_PORT`, `SMTP_SECURE`, `SMTP_USER`, `SMTP_PASS`, `SMTP_FROM`, `ENQUIRY_TO`.

## Blob storage
The admin uploader stores images in the configured container and uses the blob URL in project records. Configure the storage container for public blob reads or replace the public-URL approach with SAS/CDN delivery before launch.

## Admin
Browse to `/admin/`. Microsoft sign-in is used by Azure Static Web Apps authentication. The API additionally checks `ADMIN_EMAILS` when that setting is populated.

## Important launch note
This repository is a clean working foundation. Before publishing publicly, test the complete Azure environment: authentication, Table Storage, Blob Storage, SMTP email delivery, admin upload, custom domain, HTTPS and mobile layout.
