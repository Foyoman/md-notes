```c#
Console.WriteLine("yo whaddup");
string aFriend = "Bill";
aFriend = "Maira";
Console.WriteLine("yo " + aFriend);

string firstFriend = "Maria";
string secondFriend = "Sage";
Console.WriteLine($"My friends are {firstFriend} and {secondFriend}");
Console.WriteLine($"The name {firstFriend} has {firstFriend.Length} letters.");
Console.WriteLine($"The name {secondFriend} has {secondFriend.Length} letters.");

string greeting = "      Hello World!       ";
string trimmedGreeting = greeting.TrimStart();
trimmedGreeting = greeting.TrimEnd();
trimmedGreeting = greeting.Trim();
```
