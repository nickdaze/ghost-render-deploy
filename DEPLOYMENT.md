# Ghost 6 Deployment Instructions for Render

Your GitHub repository is ready: https://github.com/nickdaze/ghost-render-deploy

## Step-by-Step Deployment

### 1. Deploy to Render

1. Go to [Render Dashboard](https://dashboard.render.com)
2. Click the **"New +"** button in the top right
3. Select **"Blueprint"**
4. Connect your GitHub account if not already connected
5. Search for and select **`ghost-render-deploy`** repository
6. Click **"Apply"**

Render will automatically:
- Detect the `render.yaml` file
- Create the MySQL database service
- Create the Ghost web service
- Generate secure passwords
- Set up persistent storage

### 2. Monitor Deployment

The deployment will take 5-10 minutes:
1. MySQL database will deploy first
2. Ghost will deploy once MySQL is ready
3. Check the logs for each service to monitor progress

### 3. Access Your Ghost Site

Once deployed:
1. Find your Ghost service URL in the Render dashboard
   - It will be something like: `https://ghost-blog-xxxx.onrender.com`
2. Access the admin panel at: `https://ghost-blog-xxxx.onrender.com/ghost`
3. Complete the Ghost setup wizard:
   - Create your admin account
   - Configure site title and description
   - Set your timezone

### 4. Configure Custom Domain (Optional)

1. In Render Dashboard, go to your Ghost service
2. Click on **"Settings"**
3. Add your custom domain
4. Update DNS records as instructed
5. Update the `url` environment variable to your custom domain:
   - Go to **"Environment"** tab
   - Edit `url` variable
   - Set it to `https://yourdomain.com`
   - Save and redeploy

### 5. Configure Email (Optional)

To enable email for newsletters and password resets:

1. Sign up for [Mailgun](https://www.mailgun.com) (free tier available)
2. Get your Mailgun credentials
3. In Render Dashboard, go to your Ghost service
4. Go to **"Environment"** tab
5. Add these environment variables:
   - `mail__transport`: `SMTP`
   - `mail__options__service`: `Mailgun`
   - `mail__options__auth__user`: Your Mailgun username
   - `mail__options__auth__pass`: Your Mailgun password
6. Save and redeploy

## Troubleshooting

### If deployment fails:
1. Check the logs for both services in Render dashboard
2. Ensure MySQL service is running before Ghost starts
3. Verify environment variables are set correctly

### Common issues:
- **Ghost can't connect to database**: Wait for MySQL to fully initialize
- **"502 Bad Gateway"**: Ghost is still starting up, wait 2-3 minutes
- **Admin panel not accessible**: Ensure you're using `/ghost` path

## Management

### Using Render CLI:
```bash
# View services
render services

# View logs
render logs

# Restart Ghost
render restart
```

### Backup:
- Render automatically backs up your persistent disks daily
- You can also create manual backups in the dashboard

## Support

- [Ghost Documentation](https://ghost.org/docs/)
- [Render Documentation](https://render.com/docs)
- [Ghost Forum](https://forum.ghost.org/)

## Next Steps

1. Configure your content settings in Ghost admin
2. Install themes from [Ghost Marketplace](https://ghost.org/marketplace/)
3. Set up integrations (Zapier, Slack, etc.)
4. Configure membership tiers if using subscriptions
5. Start publishing!