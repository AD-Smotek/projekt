# projekt
Adam Šmotek(T3A) Todo List                                                                                                                                                                  
Vybral jsem si tohle z důvodu toho že moc neumím s javou
a chtěl jsem nějaký nádech toho jak to funguje.
Hlavně mi pomohl Matěj vít bez toho bych to nezvládl
a taky mi přišlo lepší to dělat s kamáradem než s videem,
protože mi to mohl vysvětlit a pochopil jsem to docela dobře.
Z začátku jsem moc nechápal ale postupem času jsem pochopil jak co funguje
a mám tady vysvětlení jak co funguje v tom kódu.


1. Deklarace proměnných 

javascript 

const newTodoInput = document.getElementById("new-todo"); 
const addBtn = document.getElementById("add-btn"); 
const todoList = document.getElementById("todo-list"); 
let todos = []; 

Co dělá: 

newTodoInput: Odkazuje na HTML <input> prvek, kde uživatel zadává nový úkol. 
addBtn: Odkazuje na tlačítko "Add", které přidává nový úkol do seznamu. 
todoList: Odkazuje na <ul> element, kde se zobrazují všechny úkoly jako seznam. 
todos: Je prázdné pole, které slouží k uchování všech aktuálních úkolů. 

2. Přidání nového úkolu 

javascript 

addBtn.addEventListener("click", function() { 
  const newTodoText = newTodoInput.value.trim(); 
 
  if (newTodoText !== "") { 
    todos.push(newTodoText); 
 
    newTodoInput.value = ""; 
 
    renderTodoList(); 
  } 
}); 
 

Co dělá: 

Přidává událost kliknutí (click) na tlačítko Add. 
newTodoInput.value.trim(): Získá text z pole pro zadávání a odstraní mezery na začátku a na konci. 
Kontroluje, zda text není prázdný (if (newTodoText !== "")). 
Pokud text není prázdný: 
Přidá úkol (newTodoText) do pole todos. 
Vymaže vstupní pole (newTodoInput.value = ""). 
Volá funkci renderTodoList() k aktualizaci seznamu úkolů. 

1. Deklarace proměnných 

javascript 

const newTodoInput = document.getElementById("new-todo"); 
const addBtn = document.getElementById("add-btn"); 
const todoList = document.getElementById("todo-list"); 
let todos = []; 

Co dělá: 
newTodoInput: Odkazuje na HTML <input> prvek, kde uživatel zadává nový úkol. 
addBtn: Odkazuje na tlačítko "Add", které přidává nový úkol do seznamu. 
todoList: Odkazuje na <ul> element, kde se zobrazují všechny úkoly jako seznam. 
todos: Je prázdné pole, které slouží k uchování všech aktuálních úkolů. 

3. Vykreslení seznamu úkolů 

javascript 

function renderTodoList() { 
  todoList.innerHTML = ""; 
 
  todos.forEach(function(todo, index) { 
    const li = document.createElement("li"); 
 
    li.innerText = todo; 
 
    const deleteBtn = document.createElement("button"); 
    deleteBtn.innerText = "Delete"; 
    deleteBtn.classList.add("delete-btn"); 
 
    deleteBtn.addEventListener("click", function() { 
      todos.splice(index, 1); 
 
      renderTodoList(); 
    }); 
 
    li.appendChild(deleteBtn); 
    todoList.appendChild(li); 
  }); 
} 
 

Co dělá: 
Vymaže seznam úkolů: Nastaví todoList.innerHTML = "";, aby se seznam znovu vytvořil od nuly. 
Pro každý úkol v poli todos: 
Vytvoří <li> element: 
Nastaví text úkolu jako obsah <li> (li.innerText = todo). 
Vytvoří tlačítko Delete: 
Vytvoří <button>, nastaví text "Delete" a přidá CSS třídu delete-btn. 
Přidá na tlačítko událost click, která odstraní úkol z pole todos a znovu vykreslí seznam. 
Přidá tlačítko do <li> a následně <li> do seznamu <ul>. 

 

 

4. Odstranění úkolu 

javascript 

deleteBtn.addEventListener("click", function() { 
  todos.splice(index, 1); 
 
  renderTodoList(); 
}); 
 

Co dělá: 
Událost click na tlačítku Delete: 
Použije todos.splice(index, 1) k odstranění úkolu na dané pozici index v poli todos. 
Zavolá renderTodoList() pro aktualizaci seznamu na stránce. 

 

5. Volání funkce renderTodoList() při spuštění 
javascript 
renderTodoList(); 
 

Co dělá: 

Zajistí, že seznam bude zobrazen i po načtení stránky.
Na začátku je seznam prázdný, takže funkce jen vymaže obsah todoList (který už je prázdný). 

 
Shrnutí: 
Hlavní funkce: 
addBtn.addEventListener: Přidává nový úkol do seznamu. 
renderTodoList: Aktualizuje seznam úkolů na stránce. 
deleteBtn.addEventListener: Odstraňuje úkol z pole todos. 
Klíčová logika: 
Všechna data o úkolech jsou uložena v poli todos. 
Zobrazení seznamu je dynamicky generováno na základě obsahu todos pomocí 

 
