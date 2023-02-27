# CS-210
/**
* Name: Cheikh Khouma
* Class: CS-210. Programming Languages
* Project 1
* This program will display a menu with option from 1 to 4
* 1 = add one hour
* 2 = add one minute
* 3 = add one second
* 4 = exit the program
*
*/

#include <iostream>
#include <iomanip>
#include <string>
using namespace std;

int second = 0;			//declare variable second
int hour12 = 0;			//declare variable hour12
int hour24 = 0;			//declare variable hour24
int minute = 0;			//declare variable minute
string userSelection;		//declare variable userInput
string amPm = "AM";		//declare variable amPm

void displayMenu() {									//this doesn't return anything. It only print the menu
	cout << "**************************\n";
	cout << "* 1-Add One Hour         *\n";
	cout << "* 2-Add One Minute       *\n";
	cout << "* 3-Add One Second       *\n";
	cout << "* 4-Exit Programg        *\n";
	cout << "**************************\n";
	return;

}

int addOneSecond(int secondPlus) {					//this function return value stored in secondPlus to where it was called from. it adds 1 to variable second each time it's called
	if (secondPlus >= 59) {
		secondPlus = 0;
		minute++;
	}
	else {
		secondPlus++;
	}
	return secondPlus;
}

int addOneMinute(int minutePlus) {					//this function return value stored in minutePlus to where it was called from. it adds 1 to variables hour12 and hour24 
	if (minutePlus >= 59) {							//if minutePlus ir greater or equal to 59 each time it's called
		minutePlus = 0;
		hour12++;
		hour24++;
	}
	else {
		minutePlus++;
	}
	return minutePlus;
}

int addOneHour12(int hourPlus) {				//this function return value stored in hourPlus + 1 to where it was called from. if the value passed to this function is less than
	if (hourPlus > 11) {						//11, it returns 1.
		hourPlus = 1;
		minute = 0;
		second = 0;
	}
	else {
		hourPlus++;


	}

	return hourPlus;
}

int addOneHour24(int hourPlus) {			//adds 1 to returning value as long as it's not greater or equale to 23
	if (hourPlus >= 23) {
		hourPlus = 0;
		minute = 0;
		second = 0;
	}
	else {
		hourPlus++;
	}
	return hourPlus;
}

void displayTime12(int hour, int minute, int second) {				//prints 12-hour clock using AM and PM 

	if (hour24 < 12) {
		amPm = "AM";
	}
	else {
		amPm = "PM";
	}
	cout << "**************************\n";
	cout << "*      12-Hour Clock     *\n";
	cout << "*      " << hour << ":" << minute << ":" << second << " " << amPm << "          *\n";
	cout << "**************************\n";
}

void displayTime24(int hour, int minute, int second) {				//prints 24-hour clock
	cout << "**************************\n";
	cout << "*      24-Hour Clock     *\n";
	cout << "*      " << hour << ":" << minute << ":" << second << "             *\n";
	cout << "**************************\n\n\n\n";
}

int main() {						//main function

	displayMenu();					//calls function to display menu

	cin >> userSelection;			//user input

	while (userSelection != "4") {						//loop iterates as long as number 4 isn't entered
		if (userSelection == "1") {										//if the number 1 is entered, 1 is added to hour by calling addOneHour12 and addOneHour24 functions
			hour12 = addOneHour12(hour12);
			hour24 = addOneHour24(hour24);
			displayTime12(hour12, minute, second);						//call diplayTime12 and displayTime24 to print time
			displayTime24(hour24, minute, second);
		}

		else if (userSelection == "2") {					//if the number 2 is entered, 1 is added to minute by calling addOneMinute function
			minute = addOneMinute(minute);
			displayTime12(hour12, minute, second);		//call diplayTime12 and displayTime24 to print time
			displayTime24(hour24, minute, second);
		}
		else if (userSelection == "3") {					//if the number 3 is entered, 1 is added to second by calling addOneSecond function
			second = addOneSecond(second);
			displayTime12(hour12, minute, second);		//call diplayTime12 and displayTime24 to print time
			displayTime24(hour24, minute, second);
		}
		else {
			cout << "Wrong Entry. Please try again" << endl;
		}
		displayMenu();									//prints menu each time for use to chose
		cin >> userSelection;
	}
	displayTime12(hour12, minute, second);
	displayTime24(hour24, minute, second);
}
