---
layout: post
cover: "assets/images/cover7.jpg"
navigation: True
title: R3F 시작하기-2 3D 오브젝트
date: 2023-10-16 11:30:00
tags: R3F
subclass: "post tag-test tag-content"
logo: "assets/images/ghost.png"
author: Mangb0
categories: R3F
---

## Object 선언

React Three Fiber에서는 아래와 같이 object를 선언한다.
```
<mesh>
  <boxGeometry args={[1, 1, 1]} />
  <meshBasicMaterial color={0x00ff00} />
</mesh>
```
1. 요소의 이름은 camelCase 형식이다.
2. 구성 인자값, 속성들은 props로 전달된다.

## Geometries

객체(Objecgt)는 아래와 같은 요소들로 구성되어 있다.

### Vertex

3D 공간의 점
각 점에는 3D공간의 위치를 나타내는 x,y,z 좌표를 가지고 있다.


### Edge

점을 연결하는 선
Vertex를 참조하는 집합으로 되어 있다.

### Face

Vertex를 연결하여 만든 다각형
Vertex를 참조하는 집합으로 되어 있다.

### Normal

면의 방향을 정의
빛 계산에 사용되어 빛과 Object와의 상호작용하는 방식을 결정한다.

### UV 좌표

각 Vertex에 할당된 2D 좌표 
텍스처나 이미지가 Object 표면에 매핑되는 방식을 정의

### Geometries 종류

- BoxGeometry: 상자(육면체)

```
<boxGeometry args={[5, 1, 0.2]} />
```

- SphereGeometry : 구

```
<sphereGeometry args={[1, 32, 32]} />
```

PlaneGeometry: 면
```
<planeGeometry args={[5, 5]} />
```

CylinderGeometry: 원기둥
```
<cylinderGeometry args={[1, 1, 2, 32]} />
```

자세한 설명과 값들은 [Three.js](https://threejs.org/docs/?q=geometry#api/en/geometries/BoxGeometry) 에서 확인할 수 있다.

## Materials

렌더링 시 객체 표면이 나타나는 방식을 결정한다.
객체의 색상, 질감, 투명도, 반사율등을 값을 설정하여 정의할 수 있다.

### MeshBasicMaterial

색상이나 질감을 표현
조명의 영향을 받지 않는다.
```
<mesh>
  <boxGeometry />
  <meshBasicMaterial color="green" />
</mesh>
```

### MeshStandardMaterial

색상, 질감등 속성들을 표현
조명의 영향을 받는다.
```
<mesh>
  <boxGeometry />
  <meshStandardMaterial color="green" />
</mesh>
```

### MeshToonMaterial

툰 셰이딩 Material
```
<mesh>
  <torusKnotGeometry args={[1, 0.3, 200, 32]} />
  <meshToonMaterial color="green" />
</mesh>;
```

### 이외의 Materials

이외에도 Three.js에서 제공하는 다양한 Material도 있지만
Drei 라이브러리 또한 고급 Material들을 제공하고 있다.

또한 셰이더를 사용하여 커스텀 Material도 제작 가능하다.

### Side

Side는 렌더링을 할때 Face(면)의 방향을 정의한다.
기본 세팅은 front로 설정이 되어있지만 Prop으로 THREE.DoubleSide 또는 THREE.BackSide로 설정 가능하다.

### Color

three.js는 다양한 방법으로 Color를 설정할 수 있다.
```
{
  /* Hexadecimal color */
}
<meshBasicMaterial color={0x00ff00} />;

{
  /* RGB string */
}
<meshBasicMaterial color="rgb(0, 255, 0)" />;

{
  /* X11 Color name */
}
<meshBasicMaterial color="green" />;

{
  /* Array of r, g, b values */
}
<meshBasicMaterial color={[0, 1, 0]} />;

{
  /* HSL string */
}
<meshBasicMaterial color="hsl(120, 100%, 50%)" />;
```

## Mesh

Mesh는 Geometry, Material, transformations값들로 구성되어 있다.