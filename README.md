<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>3D Modellar</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background-color: #f0f0f0;
    }
    nav {
      background-color: #333;
      padding: 1rem;
      display: flex;
      justify-content: space-around;
    }
    nav a {
      color: white;
      text-decoration: none;
      font-weight: bold;
    }
    .container {
      padding: 2rem;
      text-align: center;
    }
    canvas {
      width: 100%;
      height: 500px;
      display: block;
    }
  </style>
</head>
<body>
  <nav>
    <a href="index.html">Bosh sahifa</a>
    <a href="models.html">3D Modellar</a>
  </nav>

  <div class="container">
    <h1>3D Modellar</h1>
    <div id="scene-container"></div>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/three@0.158.0/build/three.min.js"></script>
  <script>
    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);
    const renderer = new THREE.WebGLRenderer();
    renderer.setSize(window.innerWidth, 500);
    document.getElementById('scene-container').appendChild(renderer.domElement);

    const light = new THREE.PointLight(0xffffff);
    light.position.set(10, 10, 10);
    scene.add(light);

    const geometryCube = new THREE.BoxGeometry();
    const materialCube = new THREE.MeshStandardMaterial({ color: 0x0077ff });
    const cube = new THREE.Mesh(geometryCube, materialCube);
    cube.position.x = -1.5;
    scene.add(cube);

    const geometrySphere = new THREE.SphereGeometry(0.75, 32, 32);
    const materialSphere = new THREE.MeshStandardMaterial({ color: 0xff6600 });
    const sphere = new THREE.Mesh(geometrySphere, materialSphere);
    sphere.position.x = 1.5;
    scene.add(sphere);

    camera.position.z = 5;

    function animate() {
      requestAnimationFrame(animate);
      cube.rotation.x += 0.01;
      cube.rotation.y += 0.01;
      sphere.rotation.y += 0.01;
      renderer.render(scene, camera);
    }
    animate();
  </script>
</body>
</html>
