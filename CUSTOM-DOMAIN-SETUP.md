# 🌐 Custom Domain Setup Guide

## Connecting Your Domain to SeniorCareIQ

You can use your own domain (like `seniorcareiq.com` or `www.seniorcareiq.com`) with your Netlify site!

---

## 📋 Prerequisites

- ✅ Your domain name (you have this!)
- ✅ Access to your domain registrar (where you bought the domain)
- ✅ Your Netlify site deployed and working

---

## 🚀 Quick Setup (15 Minutes)

### Step 1: Add Domain in Netlify (5 minutes)

1. **Login to Netlify**: https://app.netlify.com
2. **Select your site** (SeniorCareIQ)
3. **Go to**: Site settings → Domain management
4. **Click**: "Add custom domain"
5. **Enter your domain**: 
   - If you own `seniorcareiq.com`, enter: `seniorcareiq.com`
   - Or use subdomain: `www.seniorcareiq.com` or `app.seniorcareiq.com`
6. **Click**: "Verify"
7. **Click**: "Add domain"

### Step 2: Configure DNS (10 minutes)

Netlify will show you DNS records to add. Here's what to do:

#### Option A: Using Netlify DNS (Easiest - Recommended)

**Advantages:**
- ✅ Automatic SSL certificate
- ✅ Fastest setup
- ✅ Netlify manages everything
- ✅ One-click setup

**Steps:**
1. In Netlify domain settings, click "Use Netlify DNS"
2. Netlify will show you nameservers (like `dns1.p01.nsone.net`)
3. Copy these nameservers
4. Go to your domain registrar (see provider guides below)
5. Update nameservers to Netlify's nameservers
6. Wait 24-48 hours for DNS propagation
7. Done! Netlify handles the rest automatically

#### Option B: Keep Current DNS Provider

**Use this if:**
- You're using email with your domain
- You have other services on the domain
- You prefer your current DNS provider

**Steps:**
1. In Netlify, choose "Use external DNS"
2. Netlify will show you DNS records to add
3. Go to your domain provider's DNS settings
4. Add these records:

**For root domain (seniorcareiq.com):**
```
Type: A
Name: @
Value: 75.2.60.5
```

**For www subdomain (www.seniorcareiq.com):**
```
Type: CNAME
Name: www
Value: [your-site-name].netlify.app
```

**Example:**
If your Netlify site is `seniorcareiq-123.netlify.app`, the CNAME value is:
`seniorcareiq-123.netlify.app`

---

## 🏢 Domain Provider Specific Guides

### GoDaddy

1. **Login**: https://godaddy.com
2. **Go to**: My Products → Domains
3. **Click**: DNS next to your domain
4. **For Netlify DNS**: Scroll to Nameservers → Change → Custom → Enter Netlify nameservers
5. **For External DNS**: Click "Add" under Records → Add A and CNAME records

### Namecheap

1. **Login**: https://namecheap.com
2. **Go to**: Domain List → Manage
3. **For Netlify DNS**: Advanced DNS → Change nameservers → Custom DNS → Enter Netlify nameservers
4. **For External DNS**: Advanced DNS → Add New Record → Add A and CNAME records

### Google Domains

1. **Login**: https://domains.google.com
2. **Click** your domain
3. **Go to**: DNS
4. **For Netlify DNS**: Use custom name servers → Enter Netlify nameservers
5. **For External DNS**: Manage custom records → Add A and CNAME records

### Cloudflare

1. **Login**: https://cloudflare.com
2. **Select** your domain
3. **Go to**: DNS
4. **Add records**: Click "Add record" → Enter A and CNAME records
5. **Important**: Set proxy status to "DNS only" (grey cloud, not orange)

### Squarespace Domains

1. **Login**: https://squarespace.com
2. **Go to**: Settings → Domains
3. **Click**: Advanced Settings → Custom DNS
4. **Add**: A and CNAME records
5. **Note**: May take 24-72 hours

---

## ⚙️ DNS Records Reference

### Complete DNS Setup (Copy-Paste Ready)

**Primary domain (seniorcareiq.com):**
```
Type: A
Host: @
Points to: 75.2.60.5
TTL: Automatic
```

**WWW subdomain:**
```
Type: CNAME
Host: www
Points to: [your-netlify-site].netlify.app
TTL: Automatic
```

**Example for subdomain (app.seniorcareiq.com):**
```
Type: CNAME
Host: app
Points to: [your-netlify-site].netlify.app
TTL: Automatic
```

---

## 🔒 SSL Certificate (HTTPS)

### Automatic SSL with Netlify

1. **After DNS is configured**, go to Netlify
2. **Go to**: Site settings → Domain management → HTTPS
3. **Click**: "Verify DNS configuration"
4. **Click**: "Provision certificate"
5. **Wait**: 1-2 minutes
6. **Done**: Your site now has HTTPS! 🔒

**Netlify provides FREE SSL certificates** using Let's Encrypt.

---

## ⏱️ Propagation Times

**How long until your domain works:**
- **Netlify DNS**: 24-48 hours (usually faster)
- **External DNS**: 1-24 hours (varies by provider)
- **SSL Certificate**: 1-2 minutes after DNS verified

**Check propagation status:**
- https://www.whatsmydns.net/
- Enter your domain
- Check if it points to Netlify

---

## 🧪 Testing Your Domain

### Before DNS Propagates

1. **Preview**: Use your Netlify URL (https://[site-name].netlify.app)
2. **Works?**: Your site is ready
3. **Wait**: For DNS to propagate

### After DNS Propagates

**Test these URLs:**
- http://yourdomain.com (should redirect to HTTPS)
- https://yourdomain.com (should work)
- https://www.yourdomain.com (should work)

**All should load your SeniorCareIQ site!**

---

## 📧 Email Considerations

### Using Email with Your Domain?

**Important**: If you use email with your domain (like hello@yourdomain.com):

**Option 1: Use Netlify DNS (Recommended)**
1. Add MX records in Netlify after switching nameservers
2. Get MX records from your email provider:
   - Gmail (Google Workspace)
   - Microsoft 365
   - Zoho Mail
   - Others
3. Add them in Netlify DNS settings

**Option 2: Keep External DNS**
- Don't change nameservers
- Just add A and CNAME records for your website
- Email records stay untouched

**Email Providers - Get MX Records:**
- **Google Workspace**: https://support.google.com/a/answer/140034
- **Microsoft 365**: https://support.microsoft.com/office/
- **Zoho Mail**: https://www.zoho.com/mail/help/adminconsole/configure-email-delivery.html

---

## 🎯 Recommended Setup

### For seniorcareiq.com

**Primary domain:** `seniorcareiq.com`
**Also works:** `www.seniorcareiq.com`

**Setup:**
1. Add `seniorcareiq.com` as primary domain in Netlify
2. Netlify automatically redirects `www.seniorcareiq.com` to `seniorcareiq.com`
3. Both URLs work, users see the cleaner one

**OR**

**Primary domain:** `www.seniorcareiq.com`
**Redirects from:** `seniorcareiq.com`

**Your choice!** Most modern sites use the version without www.

---

## 🔧 Troubleshooting

### "Site not found" error

**Problem**: DNS hasn't propagated yet
**Solution**: Wait 24-48 hours, or check DNS at whatsmydns.net

### "Not secure" warning

**Problem**: SSL certificate not provisioned
**Solution**: 
1. Verify DNS is correct
2. In Netlify: HTTPS → Verify DNS → Provision certificate

### "Too many redirects"

**Problem**: Cloudflare proxy enabled with Netlify
**Solution**: In Cloudflare DNS, turn proxy off (grey cloud icon)

### Email stopped working

**Problem**: Changed nameservers but didn't add MX records
**Solution**: 
1. Get MX records from email provider
2. Add them in Netlify DNS settings

---

## 💡 Pro Tips

### 1. Use Netlify DNS
- Easier to manage
- Automatic SSL
- Faster propagation

### 2. Redirect Both Versions
- Set one as primary
- Netlify auto-redirects the other
- Better for SEO

### 3. Enable HTTPS
- Always use SSL
- Google ranks HTTPS sites higher
- Users trust the padlock icon

### 4. Monitor Uptime
- Use free tool: https://uptimerobot.com
- Get alerts if site goes down

---

## 📊 Common Domain Setups

### Setup 1: Brand New Domain
```
1. Buy domain at Namecheap/GoDaddy
2. Point nameservers to Netlify
3. Add domain in Netlify
4. Wait 24 hours
5. Done!
```

### Setup 2: Existing Domain with Email
```
1. Keep current DNS provider
2. Add A record for root domain
3. Add CNAME for www
4. Add domain in Netlify
5. Provision SSL
6. Email still works!
```

### Setup 3: Subdomain Only
```
1. Add CNAME record: app.yourdomain.com
2. Points to: your-site.netlify.app
3. Add in Netlify
4. No need to change anything else
5. Main domain unchanged
```

---

## ✅ Checklist

Before you start:
- [ ] Domain name purchased
- [ ] Login credentials for domain registrar
- [ ] Netlify site deployed and working
- [ ] Know if you use email with domain

During setup:
- [ ] Add domain in Netlify
- [ ] Choose Netlify DNS or External DNS
- [ ] Update DNS records/nameservers
- [ ] Wait for propagation

After setup:
- [ ] Test domain works
- [ ] Provision SSL certificate
- [ ] Test HTTPS works
- [ ] Verify email still works (if applicable)
- [ ] Share new domain with users!

---

## 🆘 Need Help?

**Netlify Support:**
- Docs: https://docs.netlify.com/domains-https/custom-domains/
- Community: https://answers.netlify.com/

**DNS Propagation:**
- Check: https://www.whatsmydns.net/

**Domain Provider Support:**
- Most have live chat or phone support
- Have your domain name ready

---

## 🎉 Example: Complete Setup

**Your domain**: `seniorcareiq.com`
**Netlify site**: `seniorcareiq-123.netlify.app`

### Steps:
1. ✅ Netlify → Add domain → `seniorcareiq.com`
2. ✅ Choose "Use Netlify DNS"
3. ✅ Copy nameservers from Netlify
4. ✅ GoDaddy → My Domains → DNS → Change nameservers
5. ✅ Paste Netlify nameservers
6. ✅ Save
7. ✅ Wait 24 hours
8. ✅ Netlify → HTTPS → Provision certificate
9. ✅ Done! Site live at https://seniorcareiq.com

**Total time**: 10 minutes setup + 24 hours waiting

---

**Your SeniorCareIQ site will be live at your custom domain!** 🚀
