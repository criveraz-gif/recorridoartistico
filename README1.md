<!DOCTYPE html>
<html lang="es">

<head>

<meta charset="UTF-8">

<!-- importante para celulares -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Multimedial</title>

<style>

*{
    box-sizing:border-box;
}

body{
    font-family:Arial, sans-serif;
    background:#f6f2f4;
    margin:0;
    color:#3a2b2f;
}

/* titulo */

.titulo{
    text-align:center;
    margin:30px 15px;
    font-size:clamp(28px,5vw,50px);
    color:#7a3e52;
    font-weight:normal;
}

/* contenedor pinterest */

.contenedor{
    columns:3 260px;
    column-gap:20px;
    width:95%;
    max-width:1400px;
    margin:auto;
}

/* tarjetas */

.bloque{
    background:white;
    margin:0 0 20px;
    border-radius:18px;
    overflow:hidden;
    break-inside:avoid;
    transition:0.3s ease;
    cursor:pointer;
    box-shadow:0 5px 15px rgba(0,0,0,0.05);
}

.bloque:hover{
    transform:translateY(-5px);
}

.bloque img{
    width:100%;
    display:block;
    object-fit:cover;
}

/* tamaños */

.grande img{
    height:420px;
}

.mediano img{
    height:320px;
}

.pequeno img{
    height:240px;
}

/* contenido */

.contenido{
    padding:18px;
}

.contenido h2{
    margin-top:0;
    color:#7a3e52;
    font-size:22px;
}

.contenido p{
    line-height:1.5;
    font-size:14px;
    color:#6b5b60;
}

/* modal */

.modal{
    position:fixed;
    inset:0;
    background:rgba(255,255,255,0.96);
    display:flex;
    justify-content:center;
    align-items:center;
    opacity:0;
    pointer-events:none;
    transition:0.3s;
    z-index:1000;
    padding:20px;
}

.modal.active{
    opacity:1;
    pointer-events:all;
}

.modal img{
    max-width:100%;
    max-height:90vh;
    border-radius:15px;
}

/* interactive */

.interactive{
    width:95%;
    max-width:1400px;
    margin:90px auto;
}

.interactive h2{
    text-align:center;
    color:#7a3e52;
    font-weight:normal;
    margin-bottom:35px;
    font-size:30px;
}

.grid-links{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
    gap:20px;
}

/* tarjetas links */

.link-card{
    position:relative;
    display:flex;
    align-items:center;
    justify-content:center;
    height:220px;
    border-radius:18px;
    overflow:hidden;
    text-decoration:none;
    background:#e9d8df;
    transition:0.3s;
}

.link-card:hover{
    transform:scale(1.02);
}

.link-card img{
    width:100%;
    height:100%;
    object-fit:cover;
}

.link-card span{
    position:absolute;
    bottom:15px;
    left:15px;
    color:white;
    background:rgba(122,62,82,0.7);
    padding:8px 14px;
    border-radius:10px;
    font-size:15px;
}

/* tarjeta simple */

.simple{
    color:#5a2a3b;
    font-size:18px;
    font-weight:bold;
}

/* responsive celular */

@media(max-width:700px){

    .contenedor{
        columns:1;
    }

    .grande img,
    .mediano img,
    .pequeno img{
        height:auto;
    }

    .interactive h2{
        font-size:24px;
    }

}

</style>

</head>

<body>

<h1 class="titulo">
    Recorrido artistico
</h1>

<!-- galeria -->

<div class="contenedor">

    <div class="bloque grande">

        <img src="img/mimesis.JPG" alt="mimesis">

        <div class="contenido">

            <h2>Mimesis</h2>

            <p>
                mimesis de primer año universitario.
            </p>

            <p>carton piedra de 3mm con gesso</p>

            <p>oleo</p>

            <p>17cm x 21cm </p>

        </div>

    </div>

    <div class="bloque pequeno">

        <img src="img/bodegonacuarela.JPG" alt="bodegon acuarela">

        <div class="contenido">

            <h2>Bodegon acuarela</h2>

            <p>bodegon de acuarela de primer año.</p>

            <p>papel de acuarla</p>

            <p>acuarela</p>

            <p></p>

        </div>

    </div>

    <div class="bloque mediano">

        <img src="img/perrito.jpg" alt="perrito">

        <div class="contenido">

            <h2>Perrito</h2>

            <p>Encargo personal</p>

            <p>Tela sobre bastidor</p>

            <p>Óleo</p>

            <p>40 x 40 cm</p>

        </div>

    </div>

    <div class="bloque mediano">

        <img src="img/autoretratop.jpg" alt="autoretrato">

        <div class="contenido">

            <h2>Autoretrato</h2>

            <p>Papel kraft</p>

            <p>Tinta china</p>

        </div>

    </div>

</div>

<!-- modal -->

<div class="modal" id="modal">

    <img id="modalImg" src="" alt="">

</div>

<!-- interactive -->

<section class="interactive">

    <h2>INTERACTIVE</h2>

    <div class="grid-links">

        <a href="./pagina2.html" class="link-card simple">

            Ir a la página 2

        </a>

        <a href="./obras.html" class="link-card">

            <img src="img/cuadrorojo.jpeg" alt="obra">

            <span>Obra</span>

        </a>

        <a href="./contacto.html" class="link-card">

            <img src="img/mesadetrabajo.JPG" alt="contacto">

            <span>Contacto</span>

        </a>

    </div>

</section>

<script>

/* modal */

const modal = document.getElementById("modal");
const modalImg = document.getElementById("modalImg");

document.querySelectorAll(".bloque img").forEach(img=>{

    img.addEventListener("click", ()=>{

        modal.classList.add("active");

        modalImg.src = img.src;

    });

});

modal.addEventListener("click", ()=>{

    modal.classList.remove("active");

});

/* color dinámico */

function getColor(img){

    const canvas = document.createElement("canvas");

    const ctx = canvas.getContext("2d");

    canvas.width = img.naturalWidth;
    canvas.height = img.naturalHeight;

    ctx.drawImage(img,0,0);

    const data = ctx.getImageData(
        0,
        0,
        canvas.width,
        canvas.height
    ).data;

    let r=0;
    let g=0;
    let b=0;
    let c=0;

    for(let i=0;i<data.length;i+=120){

        r += data[i];
        g += data[i+1];
        b += data[i+2];

        c++;

    }

    return{

        r:Math.floor(r/c),
        g:Math.floor(g/c),
        b:Math.floor(b/c)

    };

}

document.querySelectorAll(".bloque").forEach(b=>{

    const img = b.querySelector("img");

    const cont = b.querySelector(".contenido");

    img.onload = ()=>{

        try{

            const col = getColor(img);

            cont.style.background = `
                linear-gradient(
                    to top,
                    rgba(${col.r},${col.g},${col.b},0.25),
                    rgba(255,255,255,0.95)
                )
            `;

        }catch(e){

            console.log("error");

        }

    };

    if(img.complete){

        img.onload();

    }

});

</script>

</body>
</html>
