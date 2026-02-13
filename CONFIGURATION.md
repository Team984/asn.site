# ASN.site Configuration Guide

This guide explains how to customize your ASN.site template for your network.

## Quick Start

1. Edit `config.json` with your network details
2. Modify `index.html` if you need structural changes
3. Customize colors in `assets/css/style.css` (CSS variables in `:root`)
4. Deploy to your web server

## Configuration File (config.json)

### Network Information
```json
"network": {
  "asn": "AS64512",              // Your AS number
  "name": "EXAMPLE-NET",          // Network name
  "organization": "Example Network Operations",
  "description": "Your network description"
}
```

### IP Prefixes
```json
"prefixes": {
  "ipv4": ["203.0.113.0/24"],    // Add all your IPv4 prefixes
  "ipv6": ["2001:db8::/32"]      // Add all your IPv6 prefixes
}
```

### Registry Information
```json
"registry": {
  "irr_object": "AS-EXAMPLE",    // Your IRR AS-SET
  "peeringdb_url": "https://peeringdb.com",
  "peeringdb_id": null           // Your PeeringDB numeric ID
}
```

### Network Statistics
These appear in the hero section with animated counters.
```json
"stats": {
  "active_peers": 48,            // Number of BGP peers
  "pop_locations": 12,           // Number of PoPs
  "uptime_percent": 99.98,       // Uptime percentage
  "capacity_gbps": 100           // Total capacity in Gbps
}
```

### Peering Policy
```json
"peering": {
  "policy": "Open Peering Policy",
  "description": "Your peering policy description",
  "requirements": [              // List of requirements
    "Active 24/7 NOC",
    "Valid AS number"
  ],
  "locations": [                 // Your peering locations
    "AMS-IX Amsterdam",
    "DE-CIX Frankfurt"
  ]
}
```

### Contact Information
```json
"contact": {
  "noc": "noc@example.net",
  "peering": "peering@example.net",
  "sales": "sales@example.net",
  "abuse": "abuse@example.net"
}
```

### Looking Glass Configuration
```json
"looking_glass": {
  "enabled": true,               // Enable/disable looking glass
  "routers": [
    {
      "id": "ams",               // Router ID (used in code)
      "name": "Amsterdam",        // Display name
      "hostname": "ams.example.net"
    }
  ]
}
```

### Social Media Links
```json
"social": {
  "twitter": "https://twitter.com/yourhandle",
  "github": "https://github.com/yourorg",
  "linkedin": "https://linkedin.com/company/yourcompany"
}
```

## HTML Customization (index.html)

### Update Meta Tags
```html
<title>AS64512 - Network Operations</title>
<meta name="description" content="Your network description">
```

### Update Navigation Brand
```html
<span class="asn-label">AS64512</span>
<span class="net-name">EXAMPLE-NET</span>
```

### Update Hero Section
```html
<h1 class="hero-title">
  <span class="title-line">Autonomous System</span>
  <span class="title-line accent">64512</span>
</h1>
<p class="hero-subtitle">Your network tagline</p>
```

### Update Network Information Cards
Modify the info-card sections with your actual data:
```html
<div class="info-value">AS64512</div>
<div class="info-value">203.0.113.0/24</div>
```

## CSS Customization (assets/css/style.css)

### Color Scheme
Edit CSS variables in `:root` for dark theme:
```css
:root {
    --primary: #00ff88;           /* Primary accent color */
    --secondary: #0099ff;         /* Secondary accent color */
    --background: #0a0e17;        /* Page background */
    --surface: #131825;           /* Card backgrounds */
    --text-primary: #e8ecf5;      /* Main text color */
}
```

Edit `[data-theme="light"]` for light theme colors.

### Typography
Change fonts by updating the Google Fonts import:
```css
@import url('https://fonts.googleapis.com/css2?family=YourFont&display=swap');

body {
    font-family: 'YourFont', sans-serif;
}
```

### Animations
Disable animations by removing or modifying animation properties:
```css
.hero-content {
    animation: none;  /* Disable animation */
}
```

## JavaScript Features (assets/js/main.js)

### Theme Toggle
The theme toggle saves preference to localStorage.
Default theme is set in config.json.

### Stat Counters
Animated counters start when scrolled into view.
Values come from HTML data-count attributes.

### Network Canvas
Animated network visualization in hero section.
Disable by setting `features.network_animation: false` in config.

### Looking Glass
Demo implementation showing example output.
For production, integrate with your actual LG backend API.

## Deployment

### Static Hosting
Upload all files to your web server:
- index.html (root)
- assets/ (directory)
- config.json

### Web Server Configuration

#### Nginx
```nginx
server {
    listen 80;
    server_name as64512.example.net;
    root /var/www/asn.site;
    index index.html;
    
    location / {
        try_files $uri $uri/ =404;
    }
    
    location ~* \.(css|js|json)$ {
        expires 7d;
        add_header Cache-Control "public, immutable";
    }
}
```

#### Apache
```apache
<VirtualHost *:80>
    ServerName as64512.example.net
    DocumentRoot /var/www/asn.site
    
    <Directory /var/www/asn.site>
        Options -Indexes +FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

### Performance Optimization

1. Minify CSS and JS files
2. Enable gzip compression
3. Set proper cache headers
4. Consider CDN for Font Awesome
5. Optimize images if you add any

### Security Headers
Add security headers to your web server:
```
X-Frame-Options: SAMEORIGIN
X-Content-Type-Options: nosniff
X-XSS-Protection: 1; mode=block
Referrer-Policy: strict-origin-when-cross-origin
```

## Integration with Looking Glass

To integrate with a real looking glass backend:

1. Update the `executeLGCommand()` function in main.js
2. Replace setTimeout with actual API calls
3. Example:
```javascript
fetch(`/api/lg/${command}`, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ target, router })
})
.then(response => response.json())
.then(data => {
    lgOutput.innerHTML = `<pre>${data.output}</pre>`;
});
```

## Maintenance

### Regular Updates
- Keep Font Awesome CDN link updated
- Update contact information
- Refresh network statistics
- Update peering locations

### Monitoring
- Monitor page load times
- Check for console errors
- Test on multiple browsers
- Validate responsive design

## Support

For issues or questions:
- GitHub: Check repository issues
- Documentation: README.md
- Community: Network operator forums

## License

MIT License - See LICENSE file for details

