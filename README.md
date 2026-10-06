# contacto.ervia.tech — Tarjeta digital de Elias Ruiz

Estructura:
- Dockerfile        → imagen nginx:alpine
- nginx.conf        → sirve el .vcf como text/vcard (necesario para iPhone)
- site/index.html   → la página
- site/elias.vcf    → la ficha de contacto (con foto)
- site/*.png|jpg    → foto, logo, iconos

Despliegue en Dokploy:
1. Cloudflare → DNS → registro A `contacto` → IP del VPS, proxy en "DNS only" (nube gris).
2. Sube esta carpeta a un repo de GitHub (p. ej. EliasRuiz69/contacto-ervia).
3. Dokploy → proyecto → Create Service → Application → GitHub → repo + rama main.
4. Build Type: Dockerfile (ruta: Dockerfile). Deploy.
5. Domains → Add: host contacto.ervia.tech, path /, container port 80, HTTPS on, certificado Let's Encrypt.
6. Prueba: https://contacto.ervia.tech/elias.vcf debe abrir la ficha en iPhone.

Editar datos: cambia site/elias.vcf y/o site/index.html, haz push y redeploy.
