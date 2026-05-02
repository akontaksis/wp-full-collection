# WordPress Full API Collection

Πλήρες Bruno collection για WordPress & WooCommerce REST API testing.

Περιέχει **106 requests** σε 22 κατηγορίες — CRUD operations και security audit.

---

## Εγκατάσταση

### 1. Κατέβασε το Bruno
[https://www.usebruno.com](https://www.usebruno.com)

### 2. Clone το repo
```bash
git clone https://github.com/akontaksis/wp-full-collection.git
```

### 3. Άνοιξε στο Bruno
Bruno → **Open Collection** → επέλεξε τον φάκελο `wp-full-collection`

### 4. Ρύθμισε το Environment
Πάνω δεξιά dropdown → **production** → βάλε τα στοιχεία σου:

```
base_url      https://yoursite.com
username      admin
app_password  xxxx xxxx xxxx xxxx xxxx xxxx
```

**Πώς φτιάχνεις Application Password:**
WordPress Admin → Users → Profile → Application Passwords → Add New

---

## Δομή Collection

### WordPress Core
| Κατηγορία | Περιγραφή |
|-----------|-----------|
| 01-wordpress-posts | GET, POST, PUT, DELETE posts |
| 02-wordpress-pages | GET, POST, PUT, DELETE pages |
| 03-wordpress-media | GET, PUT, DELETE media files |
| 04-wordpress-comments | GET, POST, PUT, DELETE comments |
| 05-wordpress-users | GET, POST, PUT, DELETE users |
| 06-wordpress-taxonomies | Categories, Tags |
| 07-wordpress-settings | Site settings |
| 08-wordpress-menus | Navigation menus |

### WooCommerce
| Κατηγορία | Περιγραφή |
|-----------|-----------|
| 09-woocommerce-products | Products, variations, categories, batch update |
| 10-woocommerce-orders | Orders, notes, filtering |
| 11-woocommerce-customers | Customers, order history |
| 12-woocommerce-coupons | Coupons CRUD |
| 13-woocommerce-shipping | Zones, methods |
| 14-woocommerce-tax | Tax rates, classes |
| 15-woocommerce-payment-gateways | Payment gateways |
| 16-woocommerce-reports | Sales, top sellers, totals |

### Security Audit
| Κατηγορία | Περιγραφή |
|-----------|-----------|
| 17-security-user-enumeration | User exposure tests |
| 18-security-sensitive-rest | Sensitive endpoint tests |
| 19-security-file-exposure | File & directory exposure |
| 20-security-classic-vulnerabilities | xmlrpc, wp-cron, readme κτλ |
| 21-security-elementor | Elementor endpoint tests |
| 22-security-authentication | Auth & credential tests |

---

## Security Audit

Τα security requests έχουν **`[SECURITY]`** στο όνομα τους και περιέχουν assertions.

### Πώς να τρέξεις το security audit:
1. Βεβαιώσου ότι **δεν έχεις** Auth στο environment (anonymous requests)
2. Τρέξε όλες τις κατηγορίες 17-22
3. Κοίτα τα αποτελέσματα:

| Αποτέλεσμα | Σημαίνει |
|------------|----------|
| ✅ PASS | Το endpoint είναι σωστά προστατευμένο |
| ❌ FAIL | Πρόβλημα — δες τo docs του request |

### Τι ελέγχει:
- **User Enumeration** — εκτίθενται usernames;
- **Sensitive REST** — settings, plugins, themes, orders, customers
- **File Exposure** — debug.log, wp-config backups, .env, directory listing
- **Classic Vulnerabilities** — xmlrpc, wp-cron, readme.html
- **Elementor** — system-info, globals, templates
- **Authentication** — invalid credentials, error messages

---

## Environments

| Environment | Χρήση |
|-------------|-------|
| production | Live site |
| staging | Staging site |
| local | Local development (localhost) |

> **Σημείωση:** Τα environment αρχεία δεν ανεβαίνουν στο Git (`.gitignore`).
> Φτιάξε δικό σου `environments/production.bru` τοπικά.

---

## Variables

Κάθε environment χρησιμοποιεί τις παρακάτω variables:

| Variable | Περιγραφή | Παράδειγμα |
|----------|-----------|------------|
| `base_url` | URL του site | `https://yoursite.com` |
| `username` | WordPress username | `admin` |
| `app_password` | Application Password | `xxxx xxxx xxxx` |
| `post_id` | ID υπάρχοντος post | `1` |
| `page_id` | ID υπάρχουσας page | `2` |
| `product_id` | ID υπάρχοντος product | `100` |
| `order_id` | ID υπάρχουσας παραγγελίας | `50` |
| `customer_id` | ID υπάρχοντος customer | `10` |

---

## Stack

Φτιάχτηκε για sites με:
- WordPress 6.x
- WooCommerce 8.x+
- Elementor / Elementor Pro
- Wordfence Security

---

## Άδεια

MIT License
