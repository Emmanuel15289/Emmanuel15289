import React from 'react';

interface GorraProps {
  nombre: string;
  precio: number;
  color: string;
  material: string;
  imagen: string;
}

const Gorra: React.FC<GorraProps> = ({ nombre, precio, color, material, imagen }) => {
  return (
    <div>
      <h2>{nombre}</h2>
      <p>Precio: ${precio}</p>
      <p>Color: {color}</p>
      <p>Material: {material}</p>
      <img src={imagen} alt={nombre} />
    </div>
  );
};

export default Gorra;
import React, { useState, useEffect } from 'react';
import Gorra from './Gorra';
interface Gorra {
  nombre: string;
  precio: number;
  color: string;
  material: string;
  imagen: string;
}

const GorrasLista: React.FC = () => {
  const [gorras, setGorras] = useState<Gorra[]>([]);

  useEffect(() => {
    const gorrasMock = [
      { nombre: 'Gorra 1', precio: 20, color: 'Negro', material: 'Algodón', imagen: 'gorra1.jpg' },
      { nombre: 'Gorra 2', precio: 30, color: 'Blanco', material: 'Polímero', imagen: 'gorra2.jpg' },
      { nombre: 'Gorra 3', precio: 25, color: 'Gris', material: 'Mezcla', imagen: 'gorra3.jpg' },
    ];
    setGorras(gorrasMock);
  }, []);

  return (
    <div>
      <h1>Gorras</h1>
      {gorras.map((gorra) => (
        <Gorra key={gorra.nombre} nombre={gorra.nombre} precio={gorra.precio} color={gorra.color} material={gorra.material} imagen={gorra.imagen} />
      ))}
    </div>
  );
};

export default GorrasLista;
import React from 'react';
import GorrasLista from './GorrasLista';

const App: React.FC = () => {
  return (
    <div>
      <GorrasLista />
    </div>
  );
};

export default App;
body {
  font-family: Arial, sans-serif;
}

.gorra {
  margin-bottom: 20px;
}

.gorra img {
  width: 100px;
  height: 100px;
  border-radius: 50%;
}
