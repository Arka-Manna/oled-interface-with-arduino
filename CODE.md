//# oled-interface-with-arduino
//let's learn oled display and Arduino using U8g2 library.
//code by Arka Manna
// video example " https://drive.google.com/file/d/1FCWIXwoEjPzQpLtX31d0sWCjOfWYNaNM/view?usp=sharing "
#include <Arduino.h>
#include <U8g2lib.h>

// Initialize the OLED display using Wire library
U8G2_SSD1306_128X64_NONAME_F_SW_I2C u8g2(U8G2_R0, /* clock=*/ SCL, /* data=*/ SDA, /* reset=*/ U8X8_PIN_NONE);

void setup() {
  // Initiate the display
  u8g2.begin();
}

void loop() {
  // Picture loop
  u8g2.firstPage();
  do {
    // Draw two squares (eyes)
    u8g2.drawFrame(20, 12, 20, 20); // Shifted up by 10 pixels
    u8g2.drawFrame(80, 12, 20, 20); // Shifted up by 10 pixels
    // Draw two smaller squares inside the eyes to make them look like they're smiling
    u8g2.drawBox(25, 17, 10, 10); // Shifted up by 10 pixels
    u8g2.drawBox(85, 17, 10, 10); // Shifted up by 10 pixels
    // Draw a smile
    u8g2.drawLine(50, 40, 55, 45); // Shifted up by 10 pixels
    u8g2.drawLine(55, 45, 65, 45); // Shifted up by 10 pixels
    u8g2.drawLine(65, 45, 70, 40); // Shifted up by 10 pixels
  } while ( u8g2.nextPage() );
  
  delay(1000); // Eyes open for 1 second

  // Picture loop
  u8g2.firstPage();
  do {
    // Draw two lines (closed eyes)
    u8g2.drawLine(20, 22, 40, 22); // Shifted up by 10 pixels
    u8g2.drawLine(80, 22, 100, 22); // Shifted up by 10 pixels
    // Draw two smaller lines above the closed eyes to make them look like they're squinting
    u8g2.drawLine(25, 17, 35, 17); // Shifted up by 10 pixels
    u8g2.drawLine(85, 17, 95, 17); // Shifted up by 10 pixels
    // Draw a straight line for the mouth
    u8g2.drawLine(50, 45, 70, 45); // Shifted up by 10 pixels
  } while ( u8g2.nextPage() );

  delay(500); // Eyes closed for 0.5 seconds
}
