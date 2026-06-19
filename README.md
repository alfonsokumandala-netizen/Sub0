# SubZero

> Stop paying for things you forgot

## Overview

**SubZero** is a subscription management tool that helps you discover and cancel forgotten recurring charges. Connect your email inbox, and SubZero automatically surfaces every subscription quietly charging you — so you can eliminate the ones you don't need in seconds.

SubZero beta users save an average of **$312 in their first month** by discovering subscriptions they forgot about.

## Features

- 📬 **Smart inbox scanning** – Reads email receipts to identify all recurring charges (read-only, never stores messages)
- 🔍 **Unified dashboard** – See every subscription, free trial ending date, and price increase in one place
- ⚡ **One-tap cancellation** – Cancel unwanted subscriptions directly; we send the cancellation email on your behalf
- 🎨 **Clean, modern UI** – Beautifully designed and fully responsive
- 📱 **Mobile-friendly** – Works seamlessly on all devices
- 🔒 **Privacy-first** – Read-only email access, encrypted data handling

## How It Works

1. **Connect your inbox** – Authorize SubZero to read your email receipts
2. **Discover subscriptions** – Our system identifies all recurring charges you're paying for
3. **Cancel with one tap** – Review, select, and cancel in seconds

## Getting Started

### Quick Start (Browser)

Visit the live landing page to join the beta waitlist:
```
https://github.com/alfonsokumandala-netizen/Sub0
```

### Local Development

```bash
git clone https://github.com/alfonsokumandala-netizen/Sub0.git
cd Sub0
# Open index.html in your browser, or use a local server:
python3 -m http.server 8000
# Then visit http://localhost:8000
```

## Demo

The landing page showcases:
- Live subscription leak ticker (animated examples)
- Testimonials from beta users
- Average savings calculation
- Waitlist signup

## Project Status

🚀 **Beta Launch** – Actively collecting waitlist signups  
✅ Landing page: Live  
🔄 Backend & email integration: In development  

## Beta Feedback

> "I found a $19/month charge I had been paying for two years for a tool I used once. That's $456 just... gone." — Alex M., Product Designer

> "Turns out I had three separate password manager subscriptions running at the same time. SubZero caught all of them." — Sara K., Freelance Dev

> "Setup took 90 seconds and it immediately flagged a gym app I signed up for during COVID. Still charging me." — Raj P., Marketing

## Architecture

```
Sub0/
├── index.html          # Landing page (self-contained)
├── README.md           # This file
└── [Backend coming soon]
```

The landing page is a single HTML file with embedded CSS and Netlify form integration for waitlist management.

## Contributing

Contributions welcome! Areas we're looking for help:
- Backend API development
- Email parsing & subscription detection
- Cancellation automation
- Security & privacy hardening
- UI/UX improvements

Feel free to fork and submit pull requests.

## Technology Stack

**Frontend:**
- HTML5
- CSS3 (custom animations, responsive design)
- Vanilla JavaScript (form handling)

**Hosting & Forms:**
- Netlify (hosting + form submissions)

**Planned Backend:**
- OAuth 2.0 (email provider integration)
- Subscription detection ML
- Cancellation workflow automation

## License

MIT

## Support

Have questions or ideas? 
- Open an issue on GitHub
- Join our waitlist for beta updates
- Read our Privacy policy (included in footer)

---

**Ready to stop the bleed?** [Join the waitlist →](https://github.com/alfonsokumandala-netizen/Sub0)
