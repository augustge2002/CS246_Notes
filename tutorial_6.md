## lvalue:
How to test lvalue or rvalue?
you can flip the expression, and see if it makes sense:
```cpp
int lvalue = 10;
10 = lvalue // doesn't make sense
```
So lvalue is a lvalue

```cpp
int& lvalueFunction(int& lvalue) {
	return lvalue;
};

int rvalueFunction(int lrvalue) {
	return lrvalue;
};

int rvalueFunction2(const int& lrvalue) {
	return lrvalue;
};

int main() {
	int lvalue  = rvalueFunction(10);
	rvalueFunction(10) = lvalue; // NOT FINE, everything else fine

	int lvalue2 = 15;
	lvalue = rvalueFunction(lvalue2);

	lvalue = lvalueFunction(lvalue);
	lvalueFunction(lvalue) = 6;

	int lvalue3 = rvalueFunction2(10);
	lvalue3 = rvalueFunction2(lvalue2);

	return 0;
}
```

```cpp
string a = "aa";
string b = "bb";
a + b // this is a rvalue
```

## Big Five
**Copy constructor** for Deck:
```cpp
Deck::Deck(const Deck & deckToCopy):
	currentCard{deckToCopy.getCurrentCard()}
{
	if(deckToCopy.getNextCard() != nullptr) {
		const Deck nextDeckContent = *(deckToCopy.getNextCard());
		this->nextCard = new Deck(nextDeckContent);
		this->nextCard->previousCard = this;
	}
}
```
This example is calling the copy constructor recursively (interesting)

**Copy Assignment**


****
cardDeckPartSeven

