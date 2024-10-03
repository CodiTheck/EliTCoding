# Les Pile
Une pile (Stack, en anglais) est une structure de données linéaire
qui suit le principe
**LIFO**c(Last In First Out). Cela signifie que le dernier élément ajouté
à une pile
est le premier élément retiré. Pronons l'exemple d'une **pile** d'assiettes :
on empile les assiettes les unes sur les autres, et pour prendre une assiette,
on enlève toujours la dernière assiette posée.

Les opérations fondamentales sur une pile sont :
1. **Empiler (Push)** : Ajoute un élément au sommet de la pile.
2. **Dépiler (Pop)** : Retire et retourne l'élément se trouvant au sommet
de la pile.
3. **Peek (ou Top)** : Retourne l'élément au sommet sans le retirer.
4. **Est vide ? (isEmpty)** : Vérifier si la pile est vide.

De base, le type `list` de Python réalise une pile. On empile avec la méthode
`append()` et on dépile avec la méthode `pop()`. Si une liste est utilisée
comme un booléen, par exemple comme condition d'une instruction `if`
ou `while`, elle vaut vrai si et seulement si elle n'est pas vide.

```python
my_list = []
if my_list:
    print("My list is not empty!")
else:
    print("My list is empty!")
```

> En Python, tous les objects implémentant la méthode `__len__` peuvent être
utilisés comme un booléen, et donc comme une condition.

Toutes les opérations d'une pile s'exécute en **temps constant**, c'est à dire
en **O(1)**.

## Implémentation
Les piles peuvent être implémentées de différentes manières, par exemple :
- En utilisant un **tableau dynamique**, il s'agit d'un tableau qui s'agrandit
au besoin. Le sommet de la pile est à la fin, c'est à dire le dernier
élément du tableau.
- En utilisant une **liste chaînée**, il s'agit d'une structure dans la quelle
chaque élément stocké point vers l'élément qui le précède. Dans le cas
de notre pile, chaque élément de la pile pointe vers l'élément précédent.
Donc le dernier élément (au sommet) de notre pile aura l'adresse mémoire
de l'avant dernier élément.

### en python
Même si Python implémente déjà les piles avec le type `list`, je vais quand
vous monntrer l'implémentation de façon explicite.

```python
class Stack:
    """Implementation of a stack
    """
    def __init__(self):
        self.items = []

    def push(self, item):
        """Add an new item into stack

        :param item: The new item will be added.
        """
        self.items.append(item)

    def pop(self):
        """
        Retrieve and remove the last added item.
        """
        if not self.is_empty():
            return self.items.pop()

    def peek(self):
        """
        Get the last added item without remove it.
        """
        if not self.is_empty():
            return self.items[-1]

    def is_empty(self):
        """
        Return `True`, if the number of items is equal to `0` (stack empty)
        Return `False`, otherwise (stack not empty).

        :rtype: `bool`
        """
        return len(self.items) == 0
```

Exemple d'utilisation :

```python
stack = Stack()
stack.push(1)
stack.push(2)
stack.push(3)
print(stack.pop())  # Print: 3
print(stack.peek())  # Print: 2
print(stack.is_empty())  # Print False
```

## Applications
Les piles sont utilisées dans de nombreux algorithmes et applications.
Voici quelques exemples :

1. Partage de données entre fonctions :
- Passage des arguments à des fonctions récursives.
- Gestion du contexte d'exécution dans les langages interprétés.
- Gestion des blocs et des portées des variables dans un language
de programmation.

2. Backtracking :
- Enregistrement des choix ou actions effectuées pour revenir en arrière
en cas d'échec.

3. Gestion des appels de fonctions :
Au cour de l'exécution d'un programme informatique, la pile est utilisé
pour stocker les informations sur les fonctions appelées et leur contexte.

## Problèmes algorithmiques
Quelques problèmes algorithmiques résolue avec les piles :

1. Vérification des parenthèses équilibrées :
- Problème : Déterminer si une expression contenant des parenthèses,
crochets et accolades est correctement équilibrée. C'est à dire : vérifier
si toutes les parenthèses ouvertes sont correctement fermées.
- Solution : Parcourir la chaîne, empiler les caractères ouvrants
et dépiler lorsqu'un caractère fermant correspondant est rencontré.

```python
def is_balanced(expression):
    """
    Function to check if all open characters were closed
    on an expression.

    :param expression: The expression to parse.
    :type expression: `str`
    :rtype: `bool`
    """
    stack = Stack()
    opening = "({["
    closing = ")}]"
    pairs = {")": "(", "}": "{", "]": "["}

    for char in expression:
        if char in opening:
            stack.push(char)
        elif char in closing:
            if stack.is_empty() or stack.pop() != pairs[char]:
                return False

    return stack.is_empty()
```
