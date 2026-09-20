# Flystone Interiors — Version 2

This is the production-oriented Azure Static Web Apps starter for Flystone Interiors.

## Included
- Premium responsive public website
- Flystone branding based on the uploaded reference artwork
- Project/gallery structure
- Enquiry API with email notification support
- Azure Table Storage data model for projects and enquiries
- Azure Blob Storage image upload support
- Microsoft sign-in protected admin portal
- Project create/edit/delete and publish/unpublish
- SEO basics: title, description, robots.txt, sitemap.xml
- Social links for Flystone YouTube and Instagram

## Important
The uploaded visiting-card artwork is used as a visual brand reference and source for the starter imagery. Before public launch, replace the cropped card imagery with original high-resolution project photographs and a clean transparent logo file if available.

## Azure setup
1. Create an Azure Static Web App and connect this repository.
2. Set the app location to `/` and API location to `/api`.
3. Create an Azure Storage Account.
4. Add the Storage connection string to the API application settings as `AzureWebJobsStorage`.
5. Configure these API settings:
   - `PROJECTS_TABLE=Projects`
   - `ENQUIRIES_TABLE=Enquiries`
   - `BLOB_CONTAINER=projects`
   - `ADMIN_EMAILS=your Microsoft sign-in email`
   - `SMTP_HOST`, `SMTP_PORT`, `SMTP_USER`, `SMTP_PASS`, `SMTP_FROM`
   - `ENQUIRY_TO=info@flystoneinteriors.com,flystoneinteriors@gmail.com`
6. Configure Microsoft authentication in Static Web Apps and sign in at `/admin/`.
7. Add `www.flystoneinteriors.com` as the custom domain in Static Web Apps and complete the GoDaddy DNS verification.
8. Verify HTTPS, enquiry delivery, admin upload, mobile layout and all links before launch.

## Local API
Copy `api/local.settings.json.example` to `api/local.settings.json` and fill in real values. Do not commit that file.

## Mail
Use a dedicated mailbox/app password for SMTP. Do not put mail passwords in website JavaScript.

## Next production hardening
- Add image resizing/thumbnails and a CDN strategy.
- Add CSRF/rate limiting and stronger upload MIME/size validation.
- Add full gallery management rather than only a cover image.
- Add project detail pages and SEO metadata generated from stored projects.
- Add privacy policy, cookie policy if analytics are added, and a clear enquiry consent statement.
