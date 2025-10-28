#include <M5Unified.h>
#include <BleMouse.h>

BleMouse bleMouse(M5 AirMouse, M5Stack, 100);
float gyroX, gyroY, gyroZ;

void setup() {
  auto cfg = M5.config();
  M5.begin(cfg);
  M5.Imu.begin();
  M5.Display.setRotation(1);
  M5.Display.fillScreen(BLACK);
  M5.Display.setTextSize(2);
  M5.Display.setCursor(10, 10);
  M5.Display.println(M5 AirMousenLandscape Mode);
  bleMouse.begin();
}

void loop() {
  M5.update();
  if (bleMouse.isConnected()) {
    M5.Display.setCursor(10, 50);
    M5.Display.println(Connected );
    M5.Imu.getGyroData(&gyroX, &gyroY, &gyroZ);
    int moveX = (int)(-gyroY / 6);
    int moveY = (int)(gyroX / 6);
    bleMouse.move(moveX, moveY);
    if (M5.BtnA.wasPressed()) {
      bleMouse.click(MOUSE_LEFT);
      M5.Display.setCursor(10, 70);
      M5.Display.println(Left Click );
    }
    if (M5.BtnB.wasPressed()) {
      bleMouse.click(MOUSE_RIGHT);
      M5.Display.setCursor(10, 90);
      M5.Display.println(Right Click );
    }
  } else {
    M5.Display.setCursor(10, 50);
    M5.Display.println(Waiting for BT... );
  }
  delay(20);
}

