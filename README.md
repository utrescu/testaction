# Test Actions

Repositori creat per provar d'evitar que en fer
un workflow que tingui  `push` i `pull_requet`
s'activi dues vegades en actualitzar la branca

La idea és que jo vull fer un **build** per
cada push en qualsevol branca i **build** i **deploy** en
PR.

```yaml
on:
  push:
    branches:
      - "*"
  pull_request:
    branches:
      - "*"

jobs:
  buid:
    runs-on: ubuntu-latest
    steps:
      - name: build
        run: echo "BUILD"

  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: deploy fase 1
        run: echo "DEPLOY start"
      - name: desploy fase 2
        run: echo "DEPLOY end"
```

El problema bàsic és que un `git push` en una branca
que està en pull request fa que s'executi dues vegades

![Captura de pantalla de 2022-11-24 14-13-25](https://user-images.githubusercontent.com/2011002/203793209-8c2427f0-30b4-41a5-8f12-d39c8fd82f08.png)

