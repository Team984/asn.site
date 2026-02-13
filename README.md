ASN.site - Network Operations Template

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![PeeringDB: Connected](https://img.shields.io/badge/PeeringDB-Connected-27ae60?style=flat-square)](https://peeringdb.com)
[![BGP: Global](https://img.shields.io/badge/BGP-Global_Routing-eb4d4b?style=flat-square)]()
[![IPv6: Ready](https://img.shields.io/badge/IPv6-Enabled-8e44ad?style=flat-square)]()

A production-grade website template designed specifically for Autonomous System operators and network engineers. Built with modern web standards, distinctive design, and zero dependencies beyond Font Awesome for icons.

Stop hosting your peering policy on a plain text file from 1994. Give your network the professional web presence it deserves.

## Features

### Core Functionality
- **Network Information Display** - ASN, prefixes, IRR objects, PeeringDB integration
- **Peering Policy** - Clear presentation of peering requirements and locations
- **Looking Glass Interface** - Interactive network diagnostics tool 
- **Contact Management** - Organized NOC, peering, sales, and abuse contacts
- **Responsive Design** - Works perfectly on desktop, tablet, and mobile

### Technical Features
- **Dark/Light Theme** - User preference saved to localStorage
- **Animated Statistics** - Eye-catching counters with smooth animations
- **Network Visualization** - Real-time animated network topology canvas
- **Smooth Scrolling** - Polished navigation experience
- **Zero Build Step** - Pure HTML/CSS/JS, deploy anywhere
- **Configuration File** - Easy customization via JSON

### Design Philosophy
Following professional frontend design principles with:
- Distinctive typography (Outfit + JetBrains Mono)
- Technical aesthetic suited for network infrastructure
- Bold color scheme with proper contrast
- Purposeful animations that enhance UX
- Clean, maintainable code structure

## Quick Start

### 1. Clone or Download
```bash
git clone https://github.com/Team984/asn.site.git
cd asn.site
```

### 2. Configure Your Network
Edit `config.json` with your network details:
```json
{
  "network": {
    "asn": "AS64512",
    "name": "YOUR-NET",
    "organization": "Your Organization Name"
  }
}
```

### 3. Update HTML Content
Edit `index.html` to customize:
- Network statistics (data-count attributes)
- Peering requirements and locations
- Contact email addresses
- Social media links

### 4. Deploy
Upload to your web server or use any static hosting:
- Traditional web server (Nginx, Apache)
- GitHub Pages
- Netlify
- Cloudflare Pages
- AWS S3 + CloudFront

## Project Structure

```
asn.site/
├── index.html              # Main HTML file
├── config.json             # Configuration file
├── CONFIGURATION.md        # Detailed setup guide
├── README.md              # This file
├── LICENSE                # MIT License
└── assets/
    ├── css/
    │   └── style.css      # All styles
    └── js/
        └── main.js        # All JavaScript
```

## Customization

### Basic Configuration
All basic settings are in `config.json`:
- Network information (ASN, prefixes)
- Statistics (peers, PoPs, uptime)
- Peering policy and locations
- Contact information
- Looking glass routers

### Styling
Color scheme and theme variables in `assets/css/style.css`:
```css
:root {
    --primary: #00ff88;        /* Accent color */
    --background: #0a0e17;     /* Page background */
    --surface: #131825;        /* Card backgrounds */
}
```

### Advanced
See `CONFIGURATION.md` for detailed customization including:
- Web server setup
- Theme customization
- Font changes
- Animation controls
- Looking glass integration

## Browser Support

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Dependencies

- **Font Awesome 6.5.1** - Icons (loaded from CDN)
- **Google Fonts** - Outfit and JetBrains Mono (loaded from CDN)

No build tools, no npm packages, no framework lock-in.

## Looking Glass Integration

The included looking glass is a demo with simulated output. For production use:

1. Set up a backend API for actual network commands
2. Update `executeLGCommand()` in `main.js`
3. Implement proper authentication and rate limiting
4. Consider security implications of exposing network tools

See `CONFIGURATION.md` for integration examples.

## Performance

- **Lightweight** - ~50KB total (excluding fonts)
- **Fast Loading** - No heavy frameworks
- **Optimized** - Minimal HTTP requests
- **Cacheable** - Static assets with long cache headers

## Security Considerations

- All demo data is safe to expose
- No sensitive information in config.json by default
- Implement rate limiting for looking glass
- Use HTTPS in production
- Add security headers (see CONFIGURATION.md)

## Contributing

Contributions welcome! Areas for improvement:
- Additional themes
- More animation options
- Backend integration examples
- Accessibility enhancements
- Internationalization

## License

MIT License - see LICENSE file for details.

Free to use for personal and commercial projects.

## Credits

Built for the network operator community.

Design inspired by modern web standards and network infrastructure aesthetics.

## Support

- **Documentation** - See CONFIGURATION.md
- **Issues** - GitHub issue tracker
- **Community** - Network operator forums

## Roadmap

- [ ] Additional color themes
- [ ] Backend API examples (Python, Go, Node.js)
- [ ] PeeringDB API integration
- [ ] IRR validation tools
- [ ] Traffic graphs and statistics
- [ ] BGP community documentation section

---

Built with care for network operators who appreciate good design.
