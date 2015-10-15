//# VISUALIZACION-TABLA
//Visualización de tabla que muestra el porcentaje de color en RGB de cada uno de los colores que conforman la paleta de colores //de una imagen.

//TABLA CSV (las líneas comienzan con cada color)

COLOR 1,229,89.8,212,83.1,201,78.8
COLOR 2,229,89.8,200,78.4,156,61.2
COLOR 3,201,78.8,169,66.3,128,50.2
COLOR 4,89,34.9,67,26.3,107,42.0
COLOR 5,142,55.7,124,48.6,153,60.0
COLOR 6,163,63.9,174,68.2,177,69.4
COLOR 7,186,72.9,202,79.2,192,75.3
COLOR 8,123,48.2,158,62.0,130,51.0
COLOR 9,72,28.2,106,41.6,67,26.3
COLOR 10,116,45.5,108,42.4,39,15.3
COLOR 11,117,45.9,124,48.6,72,28.2
COLOR 12,179,70.2,155,60.8,90,35.3
COLOR 13,232,91.0,196,76.9,135,52.9
COLOR 14,227,89.0,184,72.2,151,59.2
COLOR 15,195,76.5,122,47.8,94,36.9
COLOR 16,197,77.3,111,43.5,61,23.9
COLOR 17,169,66.3,30,11.8,63,24.7
COLOR 18,145,56.9,61,23.9,29,11.4
COLOR 19,191,74.9,128,50.2,66,25.9
COLOR 20,223,87.5,162,63.5,66,25.9

//LINK PARA DESCARGAR IMÁGEN

https://41.media.tumblr.com/fa4113189250e8b63ccba0772db84cee/tumblr_mfl0gsj1dS1r9ublwo1_500.jpg

// CÓDIGO

PImage hojas;
PFont escala;
Table palette;

int r,g,b;
float pr,pg,pb;

int x;
String porcentajes[]={"0%","10%","20%","30%","40%","50%","60%","70%","80%",
"90%","100%"};
float vp,da;



void setup(){
size (1200,670);
hojas= loadImage("photo.jpg");

escala= loadFont("CenturyGothic-15.vlw");
textFont (escala,10);
smooth(5);

palette= loadTable("colores.csv");
 
}

void draw(){
 
background (255); 
image(hojas, 0,0);  
stroke(180);
line(450,620,1200,620);

for(int i=0; i<600 ;i+=30){
  
  r= palette.getInt(i/30,1);
  g= palette.getInt(i/30,3);
  b= palette.getInt(i/30,5);

fill(r,g,b);
noStroke();
rect (400, i, 50,30);

  
  pr= palette.getInt(i/30,2);
  pg= palette.getInt(i/30,4);
  pb= palette.getInt(i/30,6);
  
   ////BOLITAS ROJAS
  
  fill(r,0,0);
  vp= map(r,0,255,0,100);
  da= map(r,0,255,450,1200);
  
  ellipse (da, i+15, vp/2,vp/2);
  
     ////BOLITAS VERDES
  
  fill(0,g,0);
  vp= map(g,0,255,0,100);
  da= map(g,0,255,450,1200);
  ellipse (da, i+15, vp/2,vp/2);
  
     ////BOLITAS VERDES
  
  fill(0,0,b);
  vp= map(b,0,255,0,100);
  da= map(b,0,255,450,1200);
  ellipse (da, i+15, vp/2,vp/2);
 

}

for(int x=0; x<11; x++){

  
 stroke(180);
 
  
 textFont (escala);
text(porcentajes[x],450+x*69,650);
line(450+x*70,620,450+x*70,600 );
  

}

text("PORCENTAJES RGB QUE CONFORMAN CADA COLOR" ,30, 630);
text("DE LA PALETA CORRESPONDIENTE A LA IMAGEN",30, 650);
}
