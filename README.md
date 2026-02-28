# Leno Website

This repository contains the source files for the Leno website. It is a simple static site
with the following structure:

```
index.html
details.html
css/
  styles.css
images/
js/
  script.js
```

## Usage

Open `index.html` in a web browser to view the homepage. The `details.html` page
provides additional information.

Styles are defined in `css/styles.css` and scripts in `js/script.js`.

### Scroll-triggered Picture

The site includes an image that becomes visible or animates when the user scrolls
the page. To use this feature:

1. Place your image file in the `images/` directory. For example, `images/screenshot-1.png`.
2. Add an `<img>` element in the HTML where you want it to appear, for example:
   ```html
   <img id="scroll-image" src="images/screenshot-1.png" alt="Screenshot" />
   ```
   ![Screenshot example](images/screenshot-1.png)
3. Implement a scroll listener in `js/script.js` that toggles a CSS class when
   the image comes into view. See the sample code below:
   ```js
   const img = document.getElementById('scroll-image');
   window.addEventListener('scroll', () => {
     const rect = img.getBoundingClientRect();
     if (rect.top < window.innerHeight && rect.bottom >= 0) {
       img.classList.add('visible');
     } else {
       img.classList.remove('visible');
     }
   });
   ```
4. Style the `.visible` class in `css/styles.css` to define the appearance or
   animation (e.g. fade-in or slide-in).

This creates a picture that shows or animates as the user scrolls down the page.

## Netlify deployment

You can deploy this site to Netlify using a GitHub Action included in this
repository. Steps to complete deployment:

1. In the GitHub repository settings for this project, add two repository
   secrets:
   - `NETLIFY_AUTH_TOKEN` — your Netlify personal access token.
   - `NETLIFY_SITE_ID` — the Site ID for the Netlify site you want to deploy to.

2. Once the secrets are added, any push to the `main` branch will trigger the
   GitHub Action `.github/workflows/netlify-deploy.yml`, which deploys the
   repository root (where `index.html` lives) to Netlify.

How to get the values:
- `NETLIFY_AUTH_TOKEN`: Create a personal access token in Netlify under
  User Settings → Applications → Personal access tokens.
- `NETLIFY_SITE_ID`: In your Netlify site settings, under Site information,
  copy the Site ID.

Alternative: deploy locally using the Netlify CLI

1. Install the CLI:
```bash
npm install -g netlify-cli
```
2. Run a production deploy (you must set `NETLIFY_AUTH_TOKEN` in your shell):
```bash
export NETLIFY_AUTH_TOKEN="<your-token>"
netlify deploy --prod --dir=.
```

If you want, I can add the `NETLIFY_SITE_ID` and `NETLIFY_AUTH_TOKEN` to your
repo for you — but you will need to provide the token (and confirm it's okay
to store it as a GitHub secret). Otherwise, follow the steps above to add the
secrets and the workflow will deploy automatically on push.

## Development

- Modify HTML files to update page content.
- Edit the CSS in `css/styles.css` for styling changes.
- Update JavaScript logic in `js/script.js` for interactive behavior.

## License

This project is licensed under the MIT License. See `LICENSE` for details, if present.
