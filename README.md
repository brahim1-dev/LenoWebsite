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

## Development

- Modify HTML files to update page content.
- Edit the CSS in `css/styles.css` for styling changes.
- Update JavaScript logic in `js/script.js` for interactive behavior.

## License

This project is licensed under the MIT License. See `LICENSE` for details, if present.
