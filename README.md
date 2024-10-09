# 3dtiles_cube

Example code to create a cube at Dam square, a minimal example to create 3D Tiles

Create input table 

```sql
CREATE TABLE cube (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255),
    geom GEOMETRY(GeometryZ, 4326)
);
```

Insert the cube

```sql
INSERT INTO cube (name, geom)
VALUES (
    'Test PolyhedralSurface Z',
    ST_GeomFromText(
        'POLYHEDRALSURFACE Z(
            ((4.8915607 52.37249955 0, 4.8915607 52.37340045 0, 4.8930313 52.37340045 0, 4.8930313 52.37249955 0, 4.8915607 52.37249955 0)),
            ((4.8915607 52.37249955 100, 4.8915607 52.37340045 100, 4.8930313 52.37340045 100, 4.8930313 52.37249955 100, 4.8915607 52.37249955 100)),
            ((4.8915607 52.37249955 0, 4.8915607 52.37340045 0, 4.8915607 52.37340045 100, 4.8915607 52.37249955 100, 4.8915607 52.37249955 0)),
            ((4.8930313 52.37249955 0, 4.8930313 52.37340045 0, 4.8930313 52.37340045 100, 4.8930313 52.37249955 100, 4.8930313 52.37249955 0)),
            ((4.8915607 52.37340045 0, 4.8930313 52.37340045 0, 4.8930313 52.37340045 100, 4.8915607 52.37340045 100, 4.8915607 52.37340045 0)),
            ((4.8915607 52.37249955 0, 4.8930313 52.37249955 0, 4.8930313 52.37249955 100, 4.8915607 52.37249955 100, 4.8915607 52.37249955 0))
        )',
        4326
    )
);
```

Run pg2b3dm (executables on https://github.com/Geodan/pg2b3dm/releases)

```
pg2b3dm -U postgres -h localhost -p 5432 -d postgres -t cube -c geom -a name
```

Result see https://bertt.github.io/3dtiles_cube/demo/dam

![image](https://github.com/user-attachments/assets/8b7db318-f95e-447c-87e0-3a726986e1cb)

Demo cube in France (Bedoin) https://bertt.github.io/3dtiles_cube/demo/dam

