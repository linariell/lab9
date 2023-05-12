
<h2 align="center">ФЕДЕРАЛЬНОЕ ГОСУДАРСТВЕННОЕ БЮДЖЕТНОЕ ОБРАЗОВАТЕЛЬНОЕ УЧРЕЖДЕНИЕ ВЫСШЕГО ПРОФЕССИОНАЛЬНОГО ОБРАЗОВАНИЯ <br> «САХАЛИНСКИЙ ГОСУДАРСТВЕННЫЙ УНИВЕРСИТЕТ» <br> КАФЕДРА ИНФОРМАТИКИ </h2>
<p align="center">Лабораторная работа №9 <br>
по курсу «Web-технологии, языки и средства создания web-приложений» 

<p align="center"><b>"Java Script"</b><p>
<p align="right"><b>Выполнила: </b> студентка 231 группы Витковская Полина</p>
<p  align="right"><b>Принял: </b> Соболев Е. И., старший преподователь</p>
<br>
<br>
<br>
<p align="center">Южно-Сахалинск <br> СахГУ <br> 2023</p>
<h2> Введение </h2>
<p>Лабораторные работы по дисциплине «Web-технологии, языки и средства создания web-приложений» предназначены для освоения полученных теоретических знаний на практике. Цель работы - выполнить задачи, написав решение на Java Script:  <br>
<ol>
   <li> Есть некоторая строка (var str = 'fgfggg';), что будет, если мы возьмем str[0]?
   <li>Дана функция, она принимает в качестве аргументов строки '*', '1', 'b', '1c', реализуйте ее так, что бы она вернула строку '1*b*1c'
     <li>Дано дерево, надо найти сумму всех вершин.
       <li>Нарисовать стилями полукруг.
         <li>Есть массив в котором лежат объекты с датами, отсортировать по датам.
           <li>Есть несколько слов, определить состоят ли они из одних и тех же букв('кот', 'ток', 'окт')
             <li>От них же. Числа от 1 до 100 лежат в массиве, они хаотично перемешанные, от туда изъяли одно число, надо найти, что это за число. алгоритм не должен превышать O(n^2) сложности.
               <li>Реализовать сортировку пузырьком.
                 <li>Обратная польская нотация.
                   <li>Реализовать функцию является ли слово палендром.
   </ol>
Для реализации данной работы будет использоваться Visual Studio Code. Выполнение кода будет происходить в браузере Google Chrome.
</p>
<h2>Решение задач</h2>
<code>
      //1
      var st="fgfggg";
      console.log(st[0]);
      //2
      function f(a,b,c,d)
      {
          return (b+c+a+d);
      }
      console.log(f('*',"1","b","1c"));
      //3
      class Node {
      constructor(data) {
          this.data = data; 
          this.left = null;  
          this.right = null; 
      }
      }
      class BinarySearchTree {
          constructor() {
              this.root = null; 
          }
      insert(data) {
          let newNode = new Node(data);
          if (this.root === null) {
              this.root = newNode;
          } else {
              this.insertNode(this.root, newNode); 
          }
      }
      insertNode(node, newNode) {
          if (newNode.data < node.data) {
              if (node.left === null) {
                  node.left = newNode;
              } else {
                  this.insertNode(node.left, newNode);
              }
          } else {
              if (node.right === null) {
                  node.right = newNode;
              } else {
                  this.insertNode(node.right, newNode);
              }
          }
      }	
      tempf(node)
      {
      var sum=0;
      if (node==null) return 0;
      sum+=node.data;
      sum += this.tempf(node.left) + this.tempf(node.right);
      return sum;
      }	
      VershSum()
      {
      if(this.root === null) return 0;
      var sum = this.tempf(this.root);
      return sum;
      }


      }
      var tree = 	new BinarySearchTree();
      tree.insert(1);
      tree.insert(2);
      tree.insert(3);
      console.log(tree.VershSum());
      //4
      function gr()
      {
      let style = "<style>\ndiv{\nborder: 2px solid pink;\nbackground-color: pink;\nborder-radius: 100% 0 0 100% / 50% 0 0 50%;\nwidth: 100px;\nheight: 200px;\n}\n</style>\n<div></div>";
      document.write(style)
      }
      gr();
      //5
      let array = [new Date(2003,9,20), new Date(2000,7,9), new Date(2005,1,25)];

      for(let i = 0; i < array.length; i++)
      {
          for(let j = i + 1; j < array.length; j++)
          {
              if (array[j].getTime() < array[i].getTime())
                  {
                      let temp = array[i];
                      array[i] = array[j];
                      array[j] = temp;
                  }
          }
      }

      for(let i = 0; i < array.length; i++)
      {
          console.log(array[i].toString());  
      }
      //6
      function equals(str1, str2, str3)
      {
          let temp = [];
          for(let i = 0; i < str1.length; i++) //собрать все буквы в массив
          {
              if(temp.includes(str1[i])==false)
                  temp.push(str1[i]) //добавить в конец массива
          }

          for(let i = 0; i < str2.length;i++ )
          {
              for(let j=0;j<str3.length;j++)
              {
                  if(!temp.includes(str2[i]) || !temp.includes(str3[j]) )
                  return false;
                  if( i + 1 != str2.length) i++;
                  if( j + 1 != str3.length) j++;
              }

          }
          return true;
      }
      console.log(equals('кот','кто','тко'));
      console.log(equals('кот','некот','тко'));
      //7
      function func(array)
      {
          let frst = 0;
          let scnd = 0;
          for(let i = 1; i <= 100; i++)
          {frst += i;} 
          for(let i = 0; i < array.length; i++)
          {scnd += array[i];} 

          return frst - scnd;
      }
      let arr = [];
      let x = Math.floor(Math.random() * 100); //искомое
      for(let i = 100; i > 0; i--) 
      {
          if(i != x) {arr.push(i);}
      }
      console.log(func(arr));
      //8
      function bubble(array)
      {
          for(let i = 0; i < array.length; i++)
          {
              for(let j = i + 1; j < array.length; j++) //сравниваем попарно
                  if(array[j] < array[i])
                  {
                      let temp = array[i];
                      array[i] = array[j];
                      array[j] = temp;
                  }
          }
          return array;
      }


      let test = [11,23,2,-23,1,0,2314,2]
      console.log(bubble(test));

      //9
      function ToPolish(str)
      {
      let temp = str.split(' ');
      let operands = [];
      let x,y;
      for(let i = 0; i < temp.length; i++)
      {
          switch(temp[i])
          {
              case "+":
                  let sum = 0;
                   x =  operands.pop(); //удалить последний элемент
                   y =  operands.pop();
                      sum = x+y;
                  operands.push(sum);
                  break;
              case "-":
                  x =  operands.pop();
                  y =  operands.pop();
                  let dif = x-y;
                  operands.push(dif);
                  break;
              case "*":
                  let mult = 1;
                   x =  operands.pop();
                   y =  operands.pop();
                  mult = x*y;
                  operands.push(mult);
                  break;
              case "/":
                   x =  operands.pop();
                   y =  operands.pop();
          let div =x/y;
                  operands.push(div);
                  break;
              default:
                  operands.push(parseInt(temp[i]));
                  break;
          }
      }
      return operands.pop();
  }
   console.log(ToPolish("2 2 + 2 *"));
      //10
      function Poli(str)
      {
          str = str.toLowerCase();
          str = str.replaceAll(" ");
          for(let i = 0; i < Math.floor(str.length / 2); i++)
          {
          if(str[i] != str[str.length - (i+1)])
                  return "не палиндром";
          }
          return "палиндром";
      }
      console.log(Poli("meow"));
      console.log(Poli("12321"));
</code>
<h2>Вывод</h2>
<p>В ходе лабораторной работы были изучены элементы языка Java script. Были рассмотрены способы задания переменных, операций над ними, была проведена работа с циклами и функциями. Результатом лабораторной работы является сайт с решенными задачами.</p>    

