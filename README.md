<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Maquetación – Mapa Mental</title>
<style>
html, body {
    margin: 0;
    padding: 0;
    background: #000;
    height: 100%;
    overflow: hidden;
    font-family: Arial, sans-serif;
}

#viewport {
    width: 100vw;
    height: 100vh;
    overflow: auto;
    cursor: grab;
}

#viewport:active {
    cursor: grabbing;
}

#canvas {
    position: relative;
    width: 2400px; /* ancho real grande */
    height: auto;
}

#canvas img {
    display: block;
    width: auto;
    height: auto;
    max-width: none;
}
</style>
</head>
<body>

<div id="viewport">
    <div id="canvas">
        <img src=""C:\Users\smeza\OneDrive\Documentos\GitHub\MapaMentAAAAl\NotebookLM Mind Map.png"" alt="Mapa mental">
    </div>
</div>

<script>
const viewport = document.getElementById("viewport");

let isDown = false;
let startX, startY, scrollLeft, scrollTop;

viewport.addEventListener("mousedown", e => {
    isDown = true;
    startX = e.pageX - viewport.offsetLeft;
    startY = e.pageY - viewport.offsetTop;
    scrollLeft = viewport.scrollLeft;
    scrollTop = viewport.scrollTop;
});

viewport.addEventListener("mouseleave", () => isDown = false);
viewport.addEventListener("mouseup", () => isDown = false);

viewport.addEventListener("mousemove", e => {
    if (!isDown) return;
    e.preventDefault();
    const x = e.pageX - viewport.offsetLeft;
    const y = e.pageY - viewport.offsetTop;
    const walkX = x - startX;
    const walkY = y - startY;
    viewport.scrollLeft = scrollLeft - walkX;
    viewport.scrollTop = scrollTop - walkY;
});
</script>

</body>
</html>
