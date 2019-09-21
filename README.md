## : : s p a c e 0 0 3

![space](https://github.com/nicolasbaez/space003/blob/master/space003.gif)

```processing
int cantidad=128;
int dRotacion=2;
int velocidad=1;
int maxBox=32;
float xx[]=new float[cantidad];
float yy[]=new float[cantidad];
float zz[]=new float[cantidad];
float dx[]=new float[cantidad];
float dy[]=new float[cantidad];
float dz[]=new float[cantidad];
float dv[]=new float[cantidad];
float xPos[]=new float[cantidad];
float yPos[]=new float[cantidad];
float zPos[]=new float[cantidad];
float rr[]=new float[cantidad];
float bx[]=new float[cantidad];
int cuadros=0;
int boxColor=0;
void setup() {
  background(0);
  smooth();
  size(512, 256, P3D);
  for (int i=0; i<cantidad; i++) {
    xx[i]=0;
    yy[i]=0;
    zz[i]=0;
    dx[i]=random(dRotacion)+0.1;
    dy[i]=random(dRotacion)+0.1;
    dz[i]=random(dRotacion)+0.1;
    dv[i]=random(velocidad)+1;
    xPos[i]=0;
    yPos[i]=random(height)+1;
    zPos[i]=random(height)+1;
    rr[i]=0;
    bx[i]=random(maxBox)+1;
  }
}
void draw() {
  background(0);
  stroke(0);
  for (int i=0; i<cantidad; i++) {
    fill(rr[i], 0, 0);
    pushMatrix();
    translate(xPos[i], yPos[i], zPos[i]);
    rotateX(radians(xx[i]));
    rotateY(radians(yy[i]));
    rotateZ(radians(zz[i]));
    box(bx[i]);
    popMatrix();
    xx[i]+=dx[i];
    yy[i]+=dy[i];
    zz[i]+=dz[i];
    xPos[i]+=dv[i];
    if (xPos[i]>=width) {
      boxColor=1;
      xx[i]=0;
      yy[i]=0;
      zz[i]=0;
      dx[i]=random(dRotacion)+0.1;
      dy[i]=random(dRotacion)+0.1;
      dz[i]=random(dRotacion)+0.1;
      dv[i]=random(velocidad)+1;
      xPos[i]=0;
      yPos[i]=random(height)+1;
      zPos[i]=random(height)+1;
      rr[i]=random(128, 255)+1;
      bx[i]=random(maxBox)+1;
    }
  }
  if (boxColor==1&&cuadros<=1024) {
    saveFrame("gif/space003-######.png");
    cuadros++;
    println(cuadros);
  }
}
```
