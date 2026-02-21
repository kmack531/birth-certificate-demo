# Vital Records Express – Demo Site

A **demo marketing site** for a birth certificate ordering service. This site is designed to look professional and modern while containing **intentional risk signals** for use in product demos that evaluate website quality and risk (e.g., fraud or trust scoring).

## Purpose

Use this site to demonstrate that your evaluation product correctly flags high-risk or low-quality websites based on factors such as:

- Spelling and grammar errors  
- Broken or missing links  
- Urgency/scarcity language  
- Inconsistent or suspicious content  

## How to Run

Serve the folder over HTTP. Examples:

- **Python:** `python3 -m http.server 8000` then open `http://localhost:8000`
- **Node (npx):** `npx serve .` then open the URL shown
- Open `index.html` directly in a browser (some features may vary)

## Site Structure

| Page            | Purpose                          |
|-----------------|----------------------------------|
| `index.html`    | Landing / marketing home         |
| `order.html`    | Product selection (standard/rush/overnight) |
| `checkout.html` | Personal details, shipping, payment form   |
| `confirmation.html` | Order confirmation / thank you    |
| `about.html`    | About us                         |
| `faq.html`      | FAQ                              |
| `contact.html`  | Contact info                     |
| `404.html`      | Not found (for broken links)     |

## Intentional Risk Signals (Demo Triggers)

These are included so your evaluation product can detect them during a demo.

### Spelling & grammar mistakes

- **index.html:** “Certificat” (title, body), “Offical”, “convienient”, “suport”, “gauranteed”, “officialy”, “expediated”, “buisness”, “mesure”
- **order.html:** “Certificat”, “buisness”, “Expediated”, “Recieve”
- **checkout.html:** “buisness” (in terms text)
- **confirmation.html:** “recieved”
- **about.html:** “commited”
- **faq.html:** “buisness”, “recieve”
- **contact.html:** “suport”, “buisness”

### Broken or missing links (lead to 404 or no page)

- **Footer on all pages:**  
  - Privacy Policy (`privacy.html`) – **does not exist**  
  - Terms of Service (`terms.html`) – **does not exist**  
  - Track Order (`track.html`) – **does not exist**  
  - Refund Policy (`refunds.html`) – **does not exist**  
- **confirmation.html:** “Track Your Order” points to `track.html` – **does not exist**  
- **faq.html:** “Track Order” points to `track.html` – **does not exist**  

Configure your server to serve `404.html` for unknown paths if you want a consistent “not found” experience when users hit these links.

### Other risk-adjacent content

- Urgency/scarcity: “Don’t Wait”, “Limited availability”, “Limited slots!”, “Act now to avoid delays”
- Vague “since 2010” claim with no real company backing
- Generic support email/phone (placeholder contact details)

## Notes

- No real payments or data submission; forms only navigate to the next page or confirmation.
- This is for **demo and testing only**. Do not use for real transactions or real user data.
