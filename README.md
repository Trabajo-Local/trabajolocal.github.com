<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TrabajoLocal - Bahía Blanca</title>
<style>
    /* Reset y estilo base */
    * { box-sizing: border-box; margin:0; padding:0; font-family: Arial, sans-serif; }
    body { background-color:#f5f5f5; color:#333; }
    header { text-align:center; padding:40px 20px 20px; background-color:#4CAF50; color:white; }
    header h1 { font-size:2em; margin-bottom:10px; }
    header p { font-size:1.1em; }
    .buttons { display:flex; justify-content:center; gap:20px; margin:30px 0; }
    .buttons button { padding:20px 30px; font-size:1.2em; border:none; border-radius:12px; cursor:pointer; transition:0.3s; }
    .btn-trabajadores { background-color:#FF9800; color:white; }
    .btn-trabajadores:hover { background-color:#e68a00; }
    .btn-trabajo { background-color:#2196F3; color:white; }
    .btn-trabajo:hover { background-color:#1976D2; }
    form { background-color:white; max-width:500px; margin:20px auto; padding:30px; border-radius:12px; box-shadow:0px 4px 8px rgba(0,0,0,0.1); }
    form h2 { margin-bottom:20px; color:#333; text-align:center; }
    form label { display:block; margin-top:15px; font-weight:bold; }
    form input, form select, form textarea { width:100%; padding:10px; margin-top:5px; border-radius:8px; border:1px solid #ccc; }
    form textarea { resize:vertical; }
    form button { margin-top:20px; width:100%; padding:15px; background-color:#4CAF50; color:white; font-size:1.2em; border:none; border-radius:12px; cursor:pointer; transition:0.3s; }
    form button:hover { background-color:#45a049; }
    .lanzamiento { background-color:#fff3cd; border-left:6px solid #ffeeba; padding:20px; margin:20px auto; max-width:500px; border-radius:12px; }
    footer { text-align:center; padding:20px; font-size:0.9em; color:#555; }
    @media (max-width:600px){ .buttons { flex-direction:column; } }
</style>
</head>
<body>

<header>
<h1>TrabajoLocal</h1>
<p>Encontrá trabajadores o conseguí trabajo en Bahía Blanca.</p>
</header>

<div class="buttons">
<button class="btn-trabajadores" onclick="document.getElementById('form-trabajo').scrollIntoView({behavior:'smooth'})">🔨 Busco trabajadores</button>
<button class="btn-trabajo" onclick="document.getElementById('form-perfil').scrollIntoView({behavior:'smooth'})">👷 Busco trabajo</button>
</div>

<!-- Formulario perfil del trabajador -->
<form id="form-perfil" onsubmit="enviarWhatsAppPerfil(event)">
<h2>🧑‍🔧 Crear Perfil</h2>
<label>Nombre</label>
<input type="text" id="nombre" placeholder="Tu nombre" required>

<label>Rubro</label>
<input type="text" id="rubro" placeholder="Ej.: Electricista" required>

<label>Años de experiencia</label>
<input type="number" id="experiencia" placeholder="Ej.: 3" min="0" required>

<label>Zona</label>
<input type="text" id="zona" placeholder="Ej.: Barrio Norte" required>

<label>Qué sabe hacer</label>
<textarea id="habilidades" placeholder="Breve descripción de habilidades" rows="3" required></textarea>

<label>WhatsApp</label>
<input type="tel" id="whatsappPerfil" placeholder="Ej.: 291XXXXXXX" required>

<label>Disponible</label>
<select id="disponible">
<option value="Sí">Sí</option>
<option value="No">No</option>
</select>

<button type="submit">Guardar perfil</button>
</form>

<!-- Formulario publicar trabajo -->
<form id="form-trabajo" onsubmit="enviarWhatsAppTrabajo(event)">
<h2>🔨 Publicar Trabajo</h2>
<label>Qué necesitás</label>
<textarea id="descripcionTrabajo" placeholder="Descripción del trabajo" rows="3" required></textarea>

<label>Rubro</label>
<input type="text" id="rubroTrabajo" placeholder="Ej.: Plomero" required>

<label>Zona</label>
<input type="text" id="zonaTrabajo" placeholder="Ej.: Centro" required>

<label>Días de trabajo</label>
<input type="text" id="diasTrabajo" placeholder="Ej.: Lunes a viernes" required>

<label>Pago estimado (opcional)</label>
<input type="text" id="pagoTrabajo" placeholder="Ej.: $5000/día">

<label>WhatsApp</label>
<input type="tel" id="whatsappTrabajo" placeholder="Ej.: 291XXXXXXX" required>

<p>⭐ ¿Querés destacar este aviso? (próximamente)</p>

<button type="submit">Publicar trabajo</button>
</form>

<div class="lanzamiento">
<p>📣 <strong>TrabajoLocal – Bahía Blanca</strong></p>
<p>Estamos probando una app simple para conectar personas que buscan trabajo con quienes necesitan contratar.</p>
<ul>
<li>✔ Gratis</li>
<li>✔ Local</li>
<li>✔ Contacto directo por WhatsApp</li>
</ul>
<p>Si buscás laburo o necesitás gente para trabajar, probala y contanos qué te parece.</p>
</div>

<footer>
&copy; 2026 TrabajoLocal - Bahía Blanca
</footer>

<script>
function enviarWhatsAppPerfil(e){
    e.preventDefault();
    let nombre = encodeURIComponent(document.getElementById('nombre').value);
    let rubro = encodeURIComponent(document.getElementById('rubro').value);
    let experiencia = encodeURIComponent(document.getElementById('experiencia').value);
    let zona = encodeURIComponent(document.getElementById('zona').value);
    let habilidades = encodeURIComponent(document.getElementById('habilidades').value);
    let disponible = encodeURIComponent(document.getElementById('disponible').value);
    let whatsapp = document.getElementById('whatsappPerfil').value.replace(/\D/g,''); // Solo números

    let mensaje = `Nuevo perfil de trabajador:%0ANombre: ${nombre}%0ARubro: ${rubro}%0AAños de experiencia: ${experiencia}%0AZona: ${zona}%0AQué sabe hacer: ${habilidades}%0ADisponible: ${disponible}`;

    window.open(`https://wa.me/${whatsapp}?text=${mensaje}`, '_blank');
}

function enviarWhatsAppTrabajo(e){
    e.preventDefault();
    let descripcion = encodeURIComponent(document.getElementById('descripcionTrabajo').value);
    let rubro = encodeURIComponent(document.getElementById('rubroTrabajo').value);
    let zona = encodeURIComponent(document.getElementById('zonaTrabajo').value);
    let dias = encodeURIComponent(document.getElementById('diasTrabajo').value);
    let pago = encodeURIComponent(document.getElementById('pagoTrabajo').value);
    let whatsapp = document.getElementById('whatsappTrabajo').value.replace(/\D/g,'');

    let mensaje = `Nuevo trabajo publicado:%0AQué necesitás: ${descripcion}%0ARubro: ${rubro}%0AZona: ${zona}%0ADías de trabajo: ${dias}%0APago estimado: ${pago}`;

    window.open(`https://wa.me/${whatsapp}?text=${mensaje}`, '_blank');
}
</script>

</body>
</html>
