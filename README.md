# 3dtiles_cube

Example code to create a cube at Dam square

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

Run pg2b3dm

```
pg2b3dm -U postgres -h localhost -p 5432 -d postgres -t cube -c geom -a name
```

Result see 
