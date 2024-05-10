# Les 5.2 Security, Verdieping backend

Security

Verwerk de aanbevelingen uit de workshop (waar mogelijk) in je project:
- is je software up to date? Check met `node -v` welke versie je gebruikt en gebruik de commando's `npm audit` en `npm update` om je modules te checken en bij te werken.
- sanitise alle data van buiten je eigen code met [xss](https://jsxss.com/en/index.html) en/of valideer deze met [validator.js](https://github.com/validatorjs/validator.js)
- sla een hash van wachtwoorden op met [bcryptjs](https://github.com/dcodeIO/bcrypt.js)


Bestudeer onderstaande modules en kijk waar je deze in je project kunt implementeren als dit mogelijk is en nuttig voor je feature:
- tekst URL-safe maken met [slug](https://www.npmjs.com/package/slug)
- file upload met [multer](https://www.npmjs.com/package/multer)
- sessies met [express-session](https://expressjs.com/en/resources/middleware/session.html)
- welke handige modules kun je zelf nog vinden?
