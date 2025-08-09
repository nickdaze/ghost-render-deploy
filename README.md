# Ghost 6 on Render

This repository contains the configuration to deploy Ghost 6.0 on Render with MySQL 8.

## Quick Deploy

1. Fork or clone this repository
2. Connect your GitHub account to Render
3. Create a new Blueprint instance on Render
4. Select this repository
5. Deploy!

## Services

This deployment creates:
- **Ghost Web Service**: The Ghost 6.0 blogging platform
- **MySQL Private Service**: MySQL 8 database for Ghost

## Configuration

### Database
- MySQL 8 with persistent storage
- Automatic password generation
- 10GB disk allocation

### Ghost
- Latest Ghost Docker image
- Persistent content storage
- Production-ready configuration

## Environment Variables

The following environment variables are automatically configured:
- Database connection settings
- Site URL (update this after deployment)
- Node environment (production)

### Optional: Email Configuration

To enable email (for newsletters, password resets, etc.), uncomment and configure the mail settings in `render.yaml`:
- Set up a Mailgun account
- Add your Mailgun credentials
- Redeploy the service

## Post-Deployment

1. Access your Ghost admin at: `https://your-site.onrender.com/ghost`
2. Complete the setup wizard
3. Configure your custom domain in Render dashboard
4. Update the `url` environment variable to match your domain

## Customization

### Storage Size
Adjust disk sizes in `render.yaml`:
- MySQL: `mysql-data` disk
- Ghost: `ghost-content` disk

### MySQL Configuration
Edit `mysql/my.cnf` for custom MySQL settings

## Support

- [Ghost Documentation](https://ghost.org/docs/)
- [Render Documentation](https://render.com/docs)
- [Ghost Forum](https://forum.ghost.org/)