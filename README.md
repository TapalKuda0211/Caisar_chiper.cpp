#include <iostream>
#include <string>

using namespace std;

// Fungsi untuk enkripsi
string encrypt(string text, int s) {
    string result = "";
    for (int i = 0; i < text.length(); i++) {
        if (isupper(text[i])) {
            result += char(int(text[i] + s - 65) % 26 + 65);
        } else {
            result += char(int(text[i] + s - 97) % 26 + 97);
        }
    }
    return result;
}

// Fungsi untuk dekripsi
string decrypt(string text, int s) {
    string result = "";
    for (int i = 0; i < text.length(); i++) {
        if (isupper(text[i])) {
            result += char(int(text[i] - s - 65 + 26) % 26 + 65);
        } else {
            result += char(int(text[i] - s - 97 + 26) % 26 + 97);
        }
    }
    return result;
}

int main() {
    string text;
    int s;

    cout << "Masukkan teks: ";
    getline(cin, text);
    cout << "Masukkan pergeseran: ";
    cin >> s;

    string encrypted = encrypt(text, s);
    cout << "Teks terenkripsi: " << encrypted << endl;

    string decrypted = decrypt(encrypted, s);
    cout << "Teks terdekripsi: " << decrypted << endl;

    return 0;
}
