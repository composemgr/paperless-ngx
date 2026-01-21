# Paperless-ngx

Paperless-ngx is a document management system that transforms your physical documents into a searchable online archive. It features advanced OCR, automatic tagging, full-text search, and intelligent document processing.

## Features

- **OCR Processing**: Automatic text extraction from scanned documents
- **Full-Text Search**: Fast searching across all document content
- **Automatic Tagging**: AI-powered automatic tag suggestions
- **Email Import**: Import documents directly from email
- **Mobile App**: Scan and upload documents from mobile devices
- **Custom Metadata**: Add correspondents, document types, and custom fields
- **Workflow Automation**: Automatic classification and organization
- **Multi-Format Support**: PDF, images, Office documents, and more
- **Version Control**: Track document versions and changes
- **API Access**: Full REST API for integrations

## Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/paperless-ngx/main/docker-compose.yaml" | docker compose -f - up -d
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/paperless-ngx" ~/.local/srv/docker/paperless-ngx
cd ~/.local/srv/docker/paperless-ngx
docker compose up -d
```

### Option 3: Using composemgr
```bash
composemgr install paperless-ngx
```

## Configuration

### Environment Variables

**Admin Account:**
- `APP_ADMIN_USER`: Admin username (default: admin)
- `APP_ADMIN_PASS`: Admin password (default: changeme_admin_password)

**Database:**
- `DB_USER_NAME`: Database username (default: paperless)
- `DB_USER_PASS`: Database password (default: changeme_db_password)
- `DB_CREATE_DATABASE_NAME`: Database name (default: paperless)

**Security:**
- `APP_SECRET_KEY`: Django secret key (default: changeme_secret_key)

**Email (SMTP):**
- `EMAIL_SERVER_HOST`: SMTP server (default: 172.17.0.1)
- `EMAIL_SERVER_PORT`: SMTP port (default: 587)
- `EMAIL_SERVER_LOGIN_NAME`: SMTP username
- `EMAIL_SERVER_LOGIN_PASS`: SMTP password

### Document Directories

- `./rootfs/data/consume`: Drop documents here for automatic import
- `./rootfs/data/media/documents`: Processed document storage
- `./rootfs/data/export`: Exported documents destination

### OCR Languages

Install additional OCR languages:
```yaml
environment:
  PAPERLESS_OCR_LANGUAGE: eng+deu+fra  # English, German, French
```

### Ports

- `8000`: Web interface

## Initial Setup

1. Access Paperless-ngx at `http://localhost:8000`
2. Login with admin credentials
3. Configure settings in Settings > General
4. Set up document types, correspondents, and tags
5. Configure email import (optional)
6. Set up consumption rules and workflows
7. Install mobile app and connect to server

## Document Import Methods

### 1. Consume Folder
Drop files into `./rootfs/data/consume` directory

### 2. Web Upload
Drag and drop files in the web interface

### 3. Mobile App
Use Paperless Mobile app (iOS/Android) to scan and upload

### 4. Email Import
Configure email account to automatically import attachments

### 5. FTP/SFTP (Optional)
Set up FTP server to receive documents

## Security Recommendations

- **Change Defaults**: Update admin password and secret key immediately
- **HTTPS**: Use reverse proxy with SSL/TLS
- **Two-Factor Auth**: Enable 2FA for admin accounts
- **API Keys**: Protect API keys and rotate regularly
- **Network Access**: Restrict access with firewall rules
- **Backups**: Regular encrypted backups of documents and database
- **Updates**: Keep Paperless-ngx updated for security patches

## Backup

Critical directories to backup:
- `./rootfs/db/postgres/paperless-ngx`: Database with metadata
- `./rootfs/data/media/documents`: All processed documents
- `./rootfs/data/paperless-ngx`: Application data and configuration

## Advanced Features

### Custom Classification
Configure automatic document classification:
- Create correspondents for frequent senders
- Define document types (invoices, receipts, contracts)
- Set up automatic tagging rules

### Workflows
Automate document processing:
- Automatic filing based on content
- Email notifications on new documents
- Integration with other systems via API

### Search Capabilities
- Full-text search across all documents
- Filter by date, correspondent, type, tags
- Save custom searches
- Boolean search operators

## Troubleshooting

### OCR Not Working
- Check PAPERLESS_OCR_LANGUAGE is set correctly
- Verify Tesseract is installed in container
- Review document quality and format

### Documents Not Processing
- Check consume folder permissions
- Review logs: `docker compose logs paperless-ngx`
- Verify supported file format

### Email Import Issues
- Verify SMTP settings are correct
- Check email account credentials
- Review email import logs

### Search Not Finding Documents
- Trigger manual re-indexing in admin panel
- Check document was successfully OCR'd
- Verify PostgreSQL is running properly

## Performance Optimization

- **Storage**: Use SSD for database and search index
- **RAM**: Increase for faster OCR processing
- **Workers**: Adjust number of worker processes
- **Database**: Regular VACUUM and optimization

## Documentation

- Official Documentation: https://docs.paperless-ngx.com/
- GitHub: https://github.com/paperless-ngx/paperless-ngx
- Community Forum: https://github.com/paperless-ngx/paperless-ngx/discussions

## License

Paperless-ngx is licensed under the GNU GPL v3.
