<script>
  import { T, useTask } from "@threlte/core";

  const position = [1, 2, -36];

  let speed = 0;
  useTask((delta) => {
    speed += delta;
  });

  export let isMobile;  

  const coreNucleusColor = "purple";
  const particleLightIntensity = 1;
</script>

<T.Group>
  <T.Mesh
    position={[position[0], position[1] - Math.sin(speed), position[2]]}
    rotation={[speed, speed, 0]}
  >
    <T.DodecahedronGeometry args={[0.5, 0]} />
    <T.MeshToonMaterial color={coreNucleusColor} />
  </T.Mesh>
  <T.Mesh
    position={[position[0], position[1], position[2]]}
    rotation={[speed, speed, speed]}
  >
    <T.RingGeometry args={[3, 4, 8, 8, 0]} />
    <T.MeshToonMaterial color={coreNucleusColor} />
  </T.Mesh>
  <T.Mesh
    position={[position[0], position[1], position[2]]}
    rotation={[speed, 0, speed * 2]}
  >
    <T.RingGeometry args={[3, 4, 8, 8, 0]} />
    <T.MeshPhysicalMaterial color={coreNucleusColor} />
  </T.Mesh>
  <T.Mesh
    position={[position[0], position[1], position[2]]}
    rotation={[-speed, 0, speed]}
  >
    <T.RingGeometry args={[3, 4, 8, 8, 0]} />
    <T.MeshToonMaterial color={coreNucleusColor} />
  </T.Mesh>
  <T.Mesh
    receiveShadow
    position={[position[0], -51, position[2]]}
    rotation={[0, Math.PI - 2 / 2, 0]}
  >
    <T.BoxGeometry args={[10, 100, 10]} />
    <T.MeshStandardMaterial color="white" />
  </T.Mesh>
  <T.Mesh
    position={[
      position[0] - Math.sin(speed),
      position[1] - Math.sin(speed),
      position[2] - +Math.cos(speed),
    ]}
    rotation={[speed, speed, 0]}
  >
    <T.PointLight
      position={[0, 0, 0]}
      intensity={particleLightIntensity}
      color={coreNucleusColor}
    />
    <T.OctahedronGeometry args={[0.1]} />
    <T.MeshToonMaterial color={coreNucleusColor} />
  </T.Mesh>
  <T.Mesh
    position={[
      position[0] - Math.cos(speed * 4),
      position[1] - Math.sin(speed * 2),
      position[2] - +Math.sin(speed),
    ]}
  >
    <T.PointLight
      position={[0, 0, 0]}
      intensity={particleLightIntensity}
      color={coreNucleusColor}
    />
    <T.OctahedronGeometry args={[0.05]} />
    <T.MeshToonMaterial color={coreNucleusColor} />
  </T.Mesh>
  <T.Mesh
    position={[
      position[0] - Math.cos(speed),
      position[1] - Math.sin(speed * 2),
      position[2] - +Math.cos(speed),
    ]}
  >
    <T.PointLight
      position={[0, 0, 0]}
      intensity={particleLightIntensity}
      color={coreNucleusColor}
    />
    <T.OctahedronGeometry args={[0.05]} />
    <T.MeshToonMaterial color={coreNucleusColor} />
  </T.Mesh>
  <T.Mesh
    position={[
      position[0] - Math.cos(speed * 14),
      position[1] - Math.sin(-speed),
      position[2] - +Math.cos(speed),
    ]}
  >
    <T.PointLight
      position={[0, 0, 0]}
      intensity={particleLightIntensity}
      color={coreNucleusColor}
    />
    <T.OctahedronGeometry args={[0.02]} />
    <T.MeshToonMaterial color={coreNucleusColor} />
  </T.Mesh>
  <T.Mesh
    position={[
      position[0] - Math.cos(speed),
      0,
      position[2] - +Math.sin(speed * 3),
    ]}
  >
    <T.PointLight
      position={[0, 0, 0]}
      intensity={particleLightIntensity}
      color={coreNucleusColor}
    />
    <T.OctahedronGeometry args={[0.05]} />
    <T.MeshToonMaterial color={coreNucleusColor} />
  </T.Mesh>
  <T.Mesh
    position={[
      position[0] - Math.cos(speed) - 0.5,
      position[1] + Math.sin(speed * 1),
      position[2] - +Math.sin(-speed * 3),
    ]}
  >
    <T.PointLight
      position={[0, 0, 0]}
      intensity={particleLightIntensity}
      color="blue"
    />
    <T.OctahedronGeometry args={[0.05]} />
    <T.MeshToonMaterial color={coreNucleusColor} />
  </T.Mesh>
  {#if !isMobile}
    <T.Mesh
      position={[
        position[0],
        position[1] + Math.sin(speed * 1) * Math.cos(speed),
        position[2] - +Math.sin(-speed * 3),
      ]}
    >
      <T.PointLight
        position={[0, 0, 0]}
        intensity={particleLightIntensity}
        color="blue"
      />
      <T.OctahedronGeometry args={[0.15]} />
      <T.MeshToonMaterial color={coreNucleusColor} />
    </T.Mesh>
    <T.Mesh
      position={[
        position[0],
        position[1] + Math.sin(speed * 1) + 0.6,
        position[2] - +Math.sin(-speed * 3),
      ]}
    >
      <T.PointLight
        position={[0, 0, 0]}
        intensity={particleLightIntensity}
        color="red"
      />
      <T.OctahedronGeometry args={[0.15]} />
      <T.MeshToonMaterial color={coreNucleusColor} />
    </T.Mesh>
    <T.Mesh
      position={[
        position[0] + Math.sin(-speed * 2),
        position[1] - Math.sin(speed),
        position[2] - Math.sin(-speed * 3),
      ]}
    >
      <T.PointLight
        position={[0, 0, 0]}
        intensity={particleLightIntensity}
        color={coreNucleusColor}
      />
      <T.OctahedronGeometry args={[0.08]} />
      <T.MeshToonMaterial color={coreNucleusColor} />
    </T.Mesh>
    <T.Mesh
      position={[
        position[0] + Math.sin(-speed * 2) - 2,
        0 + Math.sin(speed),
        position[2] - Math.sin(-speed * 3) + 2,
      ]}
    >
      <T.PointLight
        position={[0, 0, 0]}
        intensity={particleLightIntensity}
        color={coreNucleusColor}
      />
      <T.OctahedronGeometry args={[0.08]} />
      <T.MeshToonMaterial color={coreNucleusColor} />
    </T.Mesh>
    <T.Mesh
      position={[
        position[0] + Math.sin(-speed * 2) - 2,
        position[1] - Math.sin(speed),
        position[2] - Math.sin(-speed * 3) + 2,
      ]}
    >
      <T.PointLight
        position={[0, 0, 0]}
        intensity={particleLightIntensity}
        color={coreNucleusColor}
      />
      <T.OctahedronGeometry args={[0.08]} />
      <T.MeshToonMaterial color={coreNucleusColor} />
    </T.Mesh>
  {/if}
  <T.Mesh
    position={[
      position[0] + Math.sin(-speed * 4) - 3,
      position[1] - Math.sin(speed),
      position[2] - Math.sin(-speed * 6) + 1,
    ]}
  >
    <T.PointLight position={[0, 0, 0]} intensity={2} color={coreNucleusColor} />
    <T.OctahedronGeometry args={[0.03]} />
    <T.MeshToonMaterial color={coreNucleusColor} />
  </T.Mesh>
</T.Group>
