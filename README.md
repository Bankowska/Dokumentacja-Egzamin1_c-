# Aplikacja desktopowa w języku C#
## 1. Opis aplikacji desktopowej
Celem projektu jest stworzenie aplikacji desktopowej w technologii Windows Forms umożliwiającej:

Wprowadzanie danych adresowych.
Wybór rodzaju przesyłki (Pocztówka, List, Paczka).
Wyświetlanie ceny oraz dodatkowych informacji w zależności od wyboru użytkownika.
Walidację kodu pocztowego z odpowiednimi komunikatami.
(Opcjonalnie) zapis danych w pliku tekstowym lub bazie danych.

## 2. Funkcjonalność projektu
Formularz danych adresowych:<br>
Pola do wprowadzenia: Ulica z numerem, Kod pocztowy, Miasto.<br>
Wybór rodzaju przesyłki:<br>
Za pomocą przycisków radiowych użytkownik wybiera jedną z trzech opcji:<br>
-Pocztówka<br>
-List<br>
-Paczka<br>
Przyciski:<br>
„Sprawdź Cenę” – wyświetla cenę i obraz odpowiadający wybranej przesyłce.<br>
„Zatwierdź” – waliduje kod pocztowy i wyświetla odpowiednie komunikaty.

## 3. Środowisko programistyczne
Język programowania: C#<br>
Technologia GUI: Windows Forms<br>
IDE: Visual Studio 2022<br>
Uruchamianie aplikacji: Za pomocą przycisku Start w Visual Studio lub pliku wykonywalnego.
## 4. Toolsy
Grupa pól radiowych:

Pola radiowe: Pocztówka, List, Paczka.
Domyślnie zaznaczone pole: Pocztówka.<br>
Pola tekstowe:

Ulica z numerem, Kod pocztowy, Miasto<br>
Każde pole poprzedzone etykietą z opisem.
Przyciski:

„Sprawdź Cenę” – sprawdza wybór i wyświetla cenę oraz obraz.<br>
„Zatwierdź” – sprawdza poprawność kodu pocztowego.<br>
<img src="https://github.com/Bankowska/Dokumentacja_Egzamin1.py/blob/main/Zrzut%20ekranu%202024-12-05%20171326.png">

## 5. Kod źródłowy
```csharp

using System;
using System.Windows.Forms;

namespace PostalApp
{
    public partial class MainForm : Form
    {
        public MainForm()
        {
            InitializeComponent();

            // Przypisanie zdarzeń do przycisków
            cena.Click += cena_Click;
            zatwierdz.Click += zatwierdz_Click;
        }

        private void cena_Click(object sender, EventArgs e)
        {
            // Sprawdzenie zaznaczonego pola radiowego
            if (poczt.Checked)
            {
                tekstCena.Text = "Cena: 1 zł";
                pictureBox.Image = Properties.Resources.poczt; // obraz pocztowki
            }
            else if (list.Checked)
            {
                tekstCena.Text = "Cena: 1,5 zł";
                pictureBox.Image = Properties.Resources.list; // obraz listu
            }
            else if (paczka.Checked)
            {
                tekstCena.Text = "Cena: 10 zł";
                pictureBox.Image = Properties.Resources.paczka; // obraz paczki
            }
        }

        private void zatwierdz_Click(object sender, EventArgs e)
        {
            string text1 = text1.Text;

            if (text1.Length != 5)
            {
                MessageBox.Show("Nieprawidłowa liczba cyfr w kodzie pocztowym");
            }
            else if (!int.TryParse(text1, out _))
            {
                MessageBox.Show("Kod pocztowy powinien się składać z samych cyfr");
            }
            else
            {
                MessageBox.Show("Dane przesyłki zostały wprowadzone");
            }
        }
    }
} // w kodzie pomogl mi chat - przepraszam :)
```
## 6. Wynik działania aplikacji
Pola wyboru (Radio Buttons):

Użytkownik może zaznaczyć tylko jedno pole z trzech dostępnych: Pocztówka, List, Paczka.
Przycisk „Sprawdź Cenę”:

Wyświetla cenę oraz odpowiedni obraz dla wybranego rodzaju przesyłki.
Przycisk „Zatwierdź”:

Waliduje kod pocztowy:<br>
Kod musi zawierać dokładnie 5 cyfr.<br>
Komunikaty błędów:<br>
Nieprawidłowa liczba cyfr.<br>
Kod zawiera niecyfrowe znaki.<br>
W przypadku poprawnego kodu: „Dane przesyłki zostały wprowadzone”.
