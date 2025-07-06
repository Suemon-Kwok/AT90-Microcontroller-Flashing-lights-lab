# AT90 Microcontroller Flashing lights lab
/*
Exercise 2: Lights flashing left and right
The instruction to pause for a certain amount of time given in milliseconds is _delay_ms(). To wait for
500ms, for example, you would write the following line in your source code:
_delay_ms( 500 );
In order to use this function, you need to write the following preprocessor directives at the beginning of
your program:
#define F_CPU 8000000L
#include <util/delay.h>
Write a program that does the following:
1. All LEDs go on
2. The LEDs remain on for 500ms
3. Then the leftmost four LEDs are on, whereas the rightmost four LEDs are turned off.
4. After 500ms, all LEDs go out and remain off for 200ms.
5. Then the rightmost four LEDs are turned on, whereas the other LEDs remain off.
6. After 500ms, all LEDs go out and remain off for 200ms.
7. Repeat from step 3
*/

*
* GccApplication1.c
*
* Created: 13 / 03 / 2025 12 : 54 : 12 pm
* Author : 
* /
#define
F_CPU 8000000L // Define clock speed for _delay_ms()
#include <avr/io.h>
#include <util/delay.h>
int main(void)
{
	DDRC = 0b11111111; // Set all PORTC pins as output
	while (1)
	{
		// Step 1: All LEDs go on
		PORTC = 0b11111111; // Turn all LEDs on
		_delay_ms(500); // Wait for 500ms
		// Step 3: Leftmost 4 LEDs on, rightmost 4 LEDs off
		PORTC = 0b11110000; // Turn on leftmost 4 LEDs
		_delay_ms(500); // Wait for 500ms
		Lab 1 excerise 1, 2 and 3 Suemon Kwok 14883335
			// Step 4: All LEDs go out
			PORTC = 0b00000000; // Turn all LEDs off
		_delay_ms(200); // Wait for 200ms
		// Step 5: Rightmost 4 LEDs on
		PORTC = 0b11111111; // Turn on rightmost 4 LEDs
		_delay_ms(500); // Wait for 500ms
		// Step 6: All LEDs go out
		PORTC = 0b00000000; // Turn all LEDs off
		_delay_ms(200); // Wait for 200ms
	}
}
