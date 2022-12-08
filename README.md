# Processing-Project-6

import processing.video.*;


String PATH = "C:/Users/chino/OneDrive/Desktop/10000000_5634341126619195_7317459083171883870_n.mp4";
Movie mov;

void setup() {
  size(1000, 1000);
  frameRate(30);
  mov = new Movie(this, PATH);
  mov.play();
  mov.speed(1);
  mov.volume(1); 
  //colorMode(HSB, 10);
  background(5);
}
void movieEvent(Movie m) {
  m.read();
}
void draw() {
  mov.loadPixels();
  //image(mov, 0, 0, width, height);
  int x = width/2;
  int y = height/2;
  for(int i=0; i<100; i++) {
    int c = mov.get(x, y);
    float h = hue(c);
    float s = saturation(c);
    float b = brightness(c);
    fill(h, s, b);
    ellipse(x, y, b*10, b*10);
    x += sin(h*15) * b * 20;
    y += cos(h*15) * b * 20; 
  }
}
