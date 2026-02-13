# ASN.site - Quick Reference

## Project Overview
Production-grade website template for Autonomous System operators and network engineers. Built with pure HTML/CSS/JavaScript following modern frontend design principles.

## File Structure
```
asn.site/
├── index.html                    Main HTML page
├── config.json                   Configuration file (edit this first)
├── deploy.sh                     Deployment script
├── .htaccess                     Apache configuration
├── README.md                     Full documentation
├── CONFIGURATION.md              Detailed setup guide
├── LICENSE                       MIT License
├── assets/
│   ├── css/
│   │   └── style.css            All styles with CSS variables
│   └── js/
│       └── main.js              All JavaScript functionality
└── server-configs/
    ├── nginx.conf               Nginx configuration example
    └── apache.conf              Apache configuration example
```

## Quick Setup (3 Steps)

### 1. Edit config.json
```json
{
  "network": {
    "asn": "AS64512",              <- Your AS number
    "name": "YOUR-NET",            <- Your network name
    "organization": "Your Org"     <- Your organization
  }
}
```

### 2. Update index.html
Search and replace:
- AS64512 -> Your ASN
- EXAMPLE-NET -> Your network name
- example.net -> Your domain
- Update email addresses
- Update statistics (data-count attributes)

### 3. Deploy
```bash
./deploy.sh local      # Test locally
./deploy.sh remote     # Deploy to server
```

## Key Features

### Design
- Dark/Light theme toggle (saves to localStorage)
- Distinctive typography: Outfit + JetBrains Mono
- Network infrastructure aesthetic
- Fully responsive
- Smooth animations

### Sections
1. Hero - ASN, tagline, animated stats
2. Network Info - ASN, prefixes, IRR, PeeringDB
3. Peering - Policy, requirements, locations
4. Looking Glass - Interactive network tools (demo)
5. Contact - NOC, peering, sales, abuse

### Technical
- Zero build step required
- Pure HTML/CSS/JS
- Font Awesome for icons
- Canvas-based network visualization
- Animated statistics counters
- Smooth scroll navigation

## Color Customization

Edit CSS variables in `assets/css/style.css`:

```css
:root {
    --primary: #00ff88;           /* Main accent */
    --secondary: #0099ff;         /* Secondary accent */
    --background: #0a0e17;        /* Page background */
    --surface: #131825;           /* Cards */
    --text-primary: #e8ecf5;      /* Main text */
    --text-secondary: #8b95b0;    /* Secondary text */
}
```

## Development

### Local Testing
```bash
python3 -m http.server 8000
open http://localhost:8000
```

### Browser DevTools
- Press F12 to open developer tools
- Check Console for errors
- Use Responsive Design Mode for mobile testing

## Deployment Options

### Static Hosting (Easiest)
- GitHub Pages
- Netlify
- Cloudflare Pages
- Vercel

Just connect your repo and deploy.

### Traditional Server
- Copy files to web root
- Use provided nginx.conf or apache.conf
- Enable HTTPS with Let's Encrypt
- Set up security headers

### Using rsync
```bash
export REMOTE_HOST=user@server.com
export REMOTE_PATH=/var/www/asn.site
./deploy.sh remote
```

## Common Customizations

### Change Fonts
Edit Google Fonts import in style.css:
```css
@import url('https://fonts.googleapis.com/css2?family=YourFont&display=swap');
```

### Disable Animations
Set animation to none in style.css:
```css
.hero-content {
    animation: none;
}
```

### Update Statistics
Edit data-count attributes in index.html:
```html
<div class="stat-value" data-count="48">0</div>
```

### Change Color Scheme
Three options:
1. Edit CSS variables in :root (recommended)
2. Choose different primary/secondary colors
3. Create new theme in [data-theme="name"]

## Looking Glass Integration

The included LG is a demo. For production:

1. Set up backend API (Python/Go/Node.js)
2. Update executeLGCommand() in main.js
3. Add authentication
4. Implement rate limiting

Example API call:
```javascript
fetch('/api/lg/ping', {
    method: 'POST',
    body: JSON.stringify({ target, router })
})
```

## Performance Tips

1. Enable gzip compression on server
2. Set cache headers (configs provided)
3. Use CDN for static assets
4. Minify CSS/JS for production (optional)
5. Enable HTTP/2 on server

## Security Checklist

- [ ] Enable HTTPS
- [ ] Set security headers
- [ ] Rate limit looking glass
- [ ] Update contact emails
- [ ] Remove sensitive data from config
- [ ] Test XSS/injection protection
- [ ] Enable firewall rules

## Troubleshooting

### Site not loading?
- Check file paths are correct
- Verify web server is running
- Check browser console for errors

### Styles not applying?
- Clear browser cache
- Check CSS file path in HTML
- Verify no CSS syntax errors

### Animations not working?
- Check JavaScript console for errors
- Verify main.js is loaded
- Test in different browser

### Looking glass not working?
- It's a demo by default
- Check browser console
- Implement backend for production

## Browser Compatibility

Tested and working:
- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Mobile Safari (iOS 14+)
- Chrome Mobile

## Support Resources

- CONFIGURATION.md - Detailed setup guide
- README.md - Full documentation
- config.json - Configuration reference
- Server configs in server-configs/

## Tips for Network Operators

### Update Regularly
- Keep stats current
- Update peering locations
- Refresh contact info
- Monitor uptime statistics

### Integrate with Tools
- Link to PeeringDB profile
- Add IRR validation
- Connect to monitoring
- Embed traffic graphs

### Professional Touch
- Use professional email addresses
- Keep information accurate
- Respond to peering requests
- Maintain updated docs

## License

MIT License - Free for personal and commercial use.

---

Need help? Check CONFIGURATION.md for detailed guides.

