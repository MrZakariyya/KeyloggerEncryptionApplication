Keylogger Encryption readme
Synopsis:
This is a program that records the information from the users keyboard inputs. THe program sends the information to two seperate files: One that is plain text and the other file is encrypted. Both files are stored in different places on the computer.

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
The motivation for this project is to have white hat hackers, and software developers to gain ideas from the indie programmer community to help prevent virus from infecting computers

Installation:
The program requires a windows based enviroment in order to work. The reason being is that two of libares (Winuser.h and windows.h) is only made for a windows computer.

