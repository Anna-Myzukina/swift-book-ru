
<h1>Свифт Тур</h1>

Традиционно первая программа на новом языке должна печатать слова "Hello, world!" На экране. 
В Swift это можно сделать в одну строку:

    print("Hello, world!")
    // выведет "Hello, world!"
    
Если вы написали код на C или Objective-C, этот синтаксис кажется вам знакомым - в Swift эта строка кода представляет собой
законченную программу.Вам не нужно импортировать отдельную библиотеку для таких функций, как ввод / вывод или обработка строк.
Код, написанный в глобальной области видимости, используется в качестве точки входа в программу, 
поэтому вам не нужна функция main ().
Вам также не нужно писать точки с запятой в конце каждого оператора.
Это руководство дает вам достаточно информации, чтобы начать писать код в Swift, показывая вам, 
как выполнять различные задачи программирования.
Не беспокойтесь, если вы чего-то не понимаете - все, что написано в этой главе, 
подробно объясняется в оставшейся части этой книги.

    Для лучшего опыта откройте эту главу как playground в Xcode. 
    Playgrounds позволяют редактировать списки кодов и сразу же видеть результат.
    <a href="https://docs.swift.org/swift-book/GuidedTour/GuidedTour.playground.zip">Download Playground</a>


<h2>Простые значения</h2>

Используйте let для создания константы и var для создания переменной. 
Значение константы не нужно знать во время компиляции, но вы должны присвоить ей значение ровно один раз.
Это означает, что вы можете использовать константы для именования значения, которое вы определяете один раз, 
но используете во многих местах.

        var myVariable = 42
        myVariable = 50
        let myConstant = 42

Константа или переменная должны иметь тот же тип, что и значение, которое вы хотите присвоить ей. 
Однако вам не всегда нужно писать тип явно. 
Предоставление значения при создании константы или переменной позволяет компилятору определить его тип. 
В приведенном выше примере компилятор делает вывод, что myVariable является целым числом, 
поскольку его начальное значение является целым числом.

Если начальное значение не предоставляет достаточной информации (или если нет начального значения), 
укажите тип, написав его после переменной, разделенной двоеточием.

            let implicitInteger = 70
            let implicitDouble = 70.0
            let explicitDouble: Double = 70


    | ЭКСПЕРИМЕНТ: Создайте константу с явным типом Float и значением 4.

 Если вам нужно преобразовать значение в другой тип, явно создайте экземпляр нужного типа.

            let label = "The width is "
            let width = 94
            let widthLabel = label + String(width)
            
    
    | ЭКСПЕРИМЕНТ : Попробуйте удалить преобразование в строку из последней строки. Какая у вас ошибка?

Есть еще более простой способ добавить значения в строки: записать значение в скобках 
и написать обратную косую черту (\) перед скобками. 
Например:

      let apples = 3
      let oranges = 5
      let appleSummary = "I have \(apples) apples."  \\ выведет "I have 3 apples."
      let fruitSummary = "I have \(apples + oranges) pieces of fruit." \\ выведет "I have 8 pieces of fruit."

    | ЭКСПЕРИМЕНТ : Используйте \ (), чтобы добавить вычисление с плавающей запятой в строку 
    и добавить чье-либо имя в приветствие.

Используйте три двойных кавычки ("" ") для строк, занимающих несколько строк. 
Отступы в начале каждой строки в кавычках удаляются, если они совпадают с отступом закрывающих кавычек. 
Например:


        let quotation = """
        Even though there's whitespace to the left,
        the actual lines aren't indented.
        Except for this line.
        Double quotes (") can appear without being escaped.

        I still have \(apples + oranges) pieces of fruit.
            """
            
            
Создайте массивы и словари, используя скобки ([]), и получите доступ к их элементам, написав индекс или ключ в скобках. 
Запятая допускается после последнего элемента.


        var shoppingList = ["catfish", "water", "tulips"]
        shoppingList[1] = "bottle of water"

        var occupations = [
            "Malcolm": "Captain",
            "Kaylee": "Mechanic",
        ]
        occupations["Jayne"] = "Public Relations"

Массивы автоматически увеличиваются при добавлении элементов.

        shoppingList.append("blue paint")
        print(shoppingList)


Чтобы создать пустой массив или словарь, используйте синтаксис инициализатора.

        let emptyArray = [String]()
        let emptyDictionary = [String: Float]()



Если информация о типе может быть выведена, вы можете написать пустой массив как [] 
и пустой словарь как [:] 
- например, когда вы устанавливаете новое значение для переменной или передаете аргумент функции.


        shoppingList = []
        occupations = [:]

<h2>Контроль потока</h2>


Используйте if и switch для создания условий, а также для for-in, while и repeat-while для создания циклов. 
Круглые скобки вокруг условия или переменной цикла являются необязательными. 
фигурные скобки вокруг обязательны.


        let individualScores = [75, 43, 103, 87, 12]
        var teamScore = 0
        for score in individualScores {
            if score > 50 {
                teamScore += 3
            } else {
                teamScore += 1
            }
        }
        print(teamScore)
        // выведет "11"

В операторе if условное выражение должно быть логическим выражением - это означает, что такой код, 
как if score { ... } был бы ошибкой, а не неявным сравнением с нулем.

Вы можете использовать if и let вместе для работы со значениями, которые могут отсутствовать. 
Эти значения представлены как дополнительные. 
Необязательное значение (optional) либо содержит значение, либо содержит ноль, чтобы указать, что значение отсутствует. 
Напишите знак вопроса (?) После типа значения, чтобы пометить значение как необязательное.


        var optionalString: String? = "Hello"
        print(optionalString == nil)
        // Prints "false"

        var optionalName: String? = "John Appleseed"
        var greeting = "Hello!"
        if let name = optionalName {
            greeting = "Hello, \(name)"
        }

    ЭКСПЕРИМЕНТ Измените optionName на ноль. Какое приветствие вы получаете? Добавьте предложение else, 
    которое устанавливает другое приветствие, если optionName равно nil.
    
Если необязательное значение равно nil, условное значение равно false и код в фигурных скобках пропускается. В противном случае необязательное значение разворачивается и присваивается константе после let, что делает развернутое значение доступным внутри блока кода.

Другой способ обработки необязательных значений - предоставить значение по умолчанию, используя ?? оператор. Если необязательное значение отсутствует, вместо него используется значение по умолчанию.


      let nickName: String? = nil
      let fullName: String = "John Appleseed"
      let informalGreeting = "Hi \(nickName ?? fullName)"

Switches поддерживают любые данные и широкий спектр операций сравнения - они не ограничиваются целыми числами 
и проверками на равенство.


        let vegetable = "red pepper"
        switch vegetable {
        case "celery":
            print("Add some raisins and make ants on a log.")
        case "cucumber", "watercress":
            print("That would make a good tea sandwich.")
        case let x where x.hasSuffix("pepper"):
            print("Is it a spicy \(x)?")
        default:
            print("Everything tastes good in soup.")
        }
        // выведет "Is it a spicy red pepper?"

    ЭКСПЕРИМЕНТ Попробуйте удалить default case. Какая у вас ошибка?

Обратите внимание, как let можно использовать в шаблоне для присвоения значения, соответствующего шаблону, константе.

После выполнения кода в соответствующем switch case программа выходит из оператора switch. 
Выполнение не переходит к следующему case, поэтому нет необходимости явно прерывать switch в конце кода каждого case.



Вы используете for-in, чтобы перебирать элементы в словаре, предоставляя пару имен, 
которые будут использоваться для каждой пары ключ-значение. 
Словари представляют собой неупорядоченную коллекцию, поэтому их ключи и значения перебираются в произвольном порядке.


      let interestingNumbers = [
          "Prime": [2, 3, 5, 7, 11, 13],
          "Fibonacci": [1, 1, 2, 3, 5, 8],
          "Square": [1, 4, 9, 16, 25],
      ]
      var largest = 0
      for (kind, numbers) in interestingNumbers {
          for number in numbers {
              if number > largest {
                  largest = number
              }
          }
      }
      print(largest)
      // Prints "25"

    ЭКСПЕРИМЕНТ Добавьте еще одну переменную, чтобы отследить, какое число было наибольшим, а также какое это наибольшее число.


Используйте while, чтобы повторить блок кода, пока условие не изменится. Вместо этого условие цикла может быть в конце, гарантируя, что цикл запускается хотя бы один раз.

        var n = 2
        while n < 100 {
            n *= 2
        }
        print(n)
        // Prints "128"

        var m = 2
        repeat {
            m *= 2
        } while m < 100
        print(m)
        // Prints "128"


Вы можете держать индекс в цикле, используя .. <для создания диапазона индексов.


        var total = 0
        for i in 0..<4 {
            total += i
        }
        print(total)
        // Prints "6"


Используйте .. <, чтобы создать диапазон, в котором отсутствует его верхнее значение, и используйте ..., 
чтобы создать диапазон, который включает оба значения.


<h2>Функции и замыкания</h2>

Используйте func для объявления функции. 
Вызовите функцию, следуя ее имени со списком аргументов в скобках. 
Используйте ->, чтобы отделить имена и типы параметров от типа возвращаемого значения функции.


        func greet(person: String, day: String) -> String {
            return "Hello \(person), today is \(day)."
        }
        greet(person: "Bob", day: "Tuesday")

    ЭКСПЕРИМЕНТ Удалить параметр дня. Добавьте параметр, чтобы включить специальный ланч сегодня в приветствие.


По умолчанию функции используют имена своих параметров в качестве меток для своих аргументов. 
Напишите пользовательскую метку аргумента перед именем параметра или введите _, чтобы не использовать метку аргумента.


      func greet(_ person: String, on day: String) -> String {
          return "Hello \(person), today is \(day)."
      }
      greet("John", on: "Wednesday")


Используйте кортеж для создания составного значения, например, для возврата нескольких значений из функции. На элементы кортежа можно ссылаться либо по имени, либо по номеру.

        func calculateStatistics(scores: [Int]) -> (min: Int, max: Int, sum: Int) {
            var min = scores[0]
            var max = scores[0]
            var sum = 0

            for score in scores {
                if score > max {
                    max = score
                } else if score < min {
                    min = score
                }
                sum += score
            }

            return (min, max, sum)
        }
        let statistics = calculateStatistics(scores: [5, 3, 100, 3, 9])
        print(statistics.sum)
        // Prints "120"
        print(statistics.2)
        // Prints "120"


Функции могут быть вложенными. Вложенные функции имеют доступ к переменным, которые были объявлены во внешней функции. 
Вы можете использовать вложенные функции, чтобы организовать код в функцию, которая является длинной или сложной.


        func returnFifteen() -> Int {
            var y = 10
            func add() {
                y += 5
            }
            add()
            return y
        }
        returnFifteen()

Функции являются первоклассным типом. Это означает, что функция может возвращать другую функцию в качестве значения.

        func makeIncrementer() -> ((Int) -> Int) {
            func addOne(number: Int) -> Int {
                return 1 + number
            }
            return addOne
        }
        var increment = makeIncrementer()
        increment(7)


Функция может принимать другую функцию в качестве одного из аргументов.


      func hasAnyMatches(list: [Int], condition: (Int) -> Bool) -> Bool {
          for item in list {
              if condition(item) {
                  return true
              }
          }
          return false
      }
      func lessThanTen(number: Int) -> Bool {
          return number < 10
      }
      var numbers = [20, 19, 7, 12]
      hasAnyMatches(list: numbers, condition: lessThanTen)

На самом деле функции - это особый случай замыканий: блоки кода, которые можно вызвать позже. 
Код в замыкании имеет доступ к таким вещам, как переменные и функции, которые были доступны в области, 
в которой было создано замыкание, даже если замыкание находится в другой области, когда оно выполняется - 
вы видели пример этого уже с вложенными функциями. 
Вы можете написать замыкание без имени, заключив код в скобки ({}). 
Используйте, чтобы отделить аргументы и тип возвращаемого значения от тела.

          numbers.map({ (number: Int) -> Int in
              let result = 3 * number
              return result
          })

    ЭКСПЕРИМЕНТ Перепишите замыкание, чтобы вернуть ноль для всех нечетных чисел.


У вас есть несколько вариантов написания замыканий более кратко. 
Когда тип замыкания уже известен, такой как callback для делегата, 
вы можете опустить тип его параметров, тип возвращаемого значения или оба. 
Закрытия одного оператора неявно возвращают значение своего единственного оператора.

    let mappedNumbers = numbers.map({ number in 3 * number })
    print(mappedNumbers)
    // Prints "[60, 57, 21, 36]"

Вы можете ссылаться на параметры по номеру, а не по имени - этот подход особенно полезен при очень коротких замыканиях. Замыкание, переданное в качестве последнего аргумента функции, может появиться сразу после скобок. 
Если замыкание является единственным аргументом функции, вы можете полностью опустить скобки.


    let sortedNumbers = numbers.sorted { $0 > $1 }
    print(sortedNumbers)
    // Prints "[20, 19, 12, 7]"

<h2>Объекты и Классы</h2>

Используйте класс, за которым следует имя класса, чтобы создать класс. 
Объявление свойства в классе записывается так же, как объявление константы или переменной, 
за исключением того, что оно находится в контексте класса. 
Аналогично, объявления методов и функций пишутся одинаково.

      class Shape {
          var numberOfSides = 0
          func simpleDescription() -> String {
              return "A shape with \(numberOfSides) sides."
          }
      }


    ЭКСПЕРИМЕНТ Добавьте постоянное свойство с помощью let, и добавьте еще один метод, который принимает аргумент.

Создайте экземпляр класса, поставив скобки после имени класса. 
Используйте синтаксис доступ через точку для доступа к свойствам и методам экземпляра.

      var shape = Shape()
      shape.numberOfSides = 7
      var shapeDescription = shape.simpleDescription()

В этой версии класса Shape отсутствует что-то важное: инициализатор для настройки класса при создании экземпляра. Используйте init для его создания.

      class NamedShape {
          var numberOfSides: Int = 0
          var name: String

          init(name: String) {
              self.name = name
          }

          func simpleDescription() -> String {
              return "A shape with \(numberOfSides) sides."
          }
      }


Обратите внимание, как self используется для различения свойства name от аргумента name инициализатору. 
Аргументы инициализатору передаются как вызов функции при создании экземпляра класса. 
Каждому свойству требуется присвоенное значение - либо в его объявлении (как с numberOfSides), 
либо в инициализаторе (как с именем).


Используйте deinit, чтобы создать деинициализатор, если вам нужно выполнить некоторую очистку перед освобождением объекта.

Подклассы включают свое имя суперкласса после имени класса, разделенное двоеточием. 
Для классов не требуется подкласса любого стандартного корневого класса, 
поэтому при необходимости вы можете включить или опустить суперкласс.


Методы в подклассе, которые переопределяют реализацию суперкласса, отмечены как переопределение - переопределение метода случайно, без переопределения, определяется компилятором как ошибка. 
Компилятор также обнаруживает методы с переопределением, которые фактически не переопределяют ни один метод в суперклассе.


            class Square: NamedShape {
                var sideLength: Double

                init(sideLength: Double, name: String) {
                    self.sideLength = sideLength
                    super.init(name: name)
                    numberOfSides = 4
                }

                func area() -> Double {
                    return sideLength * sideLength
                }

                override func simpleDescription() -> String {
                    return "A square with sides of length \(sideLength)."
                }
            }
            let test = Square(sideLength: 5.2, name: "my test square")
            test.area()
            test.simpleDescription()
            
            
       ЭКСПЕРИМЕНТ 
       Создайте другой подкласс NamedShape с именем Circle, 
       который принимает радиус и имя в качестве аргументов своего инициализатора. 
       Реализуйте метод area () и simpleDescription () в классе Circle.         
            
            
В дополнение к простым свойствам, которые хранятся, свойства могут иметь геттер и сеттер.
            
               class EquilateralTriangle: NamedShape {
                var sideLength: Double = 0.0

                init(sideLength: Double, name: String) {
                    self.sideLength = sideLength
                    super.init(name: name)
                    numberOfSides = 3
                }

                var perimeter: Double {
                    get {
                        return 3.0 * sideLength
                    }
                    set {
                        sideLength = newValue / 3.0
                    }
                }

                override func simpleDescription() -> String {
                    return "An equilateral triangle with sides of length \(sideLength)."
                }
            }
            var triangle = EquilateralTriangle(sideLength: 3.1, name: "a triangle")
            print(triangle.perimeter)
            // Prints "9.3"
            triangle.perimeter = 9.9
            print(triangle.sideLength)
            // Prints "3.3000000000000003"         

В setter для perimeter новое значение имеет неявное имя newValue. Вы можете указать явное имя в скобках после set.            
            
Обратите внимание, что инициализатор для класса EquatellTriangle имеет три разных шага:
1.Установка значения свойств, которые объявляет подкласс.
2.Вызов инициализатора суперкласса.
3.Изменение значения свойств, определенных суперклассом. Любая дополнительная работа по настройке, в которой используются методы, методы получения или установки, также может быть выполнена на этом этапе.
            
            
Если вам не нужно вычислять свойство, но вам все равно нужно предоставить код, 
который запускается до и после установки нового значения, используйте willSet и didSet. 
Предоставляемый вами код запускается каждый раз, когда значение изменяется вне инициализатора. 
Например, класс ниже гарантирует, что длина стороны его треугольника всегда равна длине стороны его квадрата.            
            
           class TriangleAndSquare {
              var triangle: EquilateralTriangle {
                  willSet {
                      square.sideLength = newValue.sideLength
                  }
              }
              var square: Square {
                  willSet {
                      triangle.sideLength = newValue.sideLength
                  }
              }
              init(size: Double, name: String) {
                  square = Square(sideLength: size, name: name)
                  triangle = EquilateralTriangle(sideLength: size, name: name)
              }
          }
          var triangleAndSquare = TriangleAndSquare(size: 10, name: "another test shape")
          print(triangleAndSquare.square.sideLength)
          // Prints "10.0"
          print(triangleAndSquare.triangle.sideLength)
          // Prints "10.0"
          triangleAndSquare.square = Square(sideLength: 50, name: "larger square")
          print(triangleAndSquare.triangle.sideLength)
          // Prints "50.0"           
            
   При работе с дополнительными значениями вы можете написать? до операций, таких как методы, свойства и индексирование. 
   Если значение до? это nil, все после? игнорируется, и значение всего выражения равно nil. 
   В противном случае необязательное значение разворачивается, и все после? действует на развернутое значение. 
   В обоих случаях значение всего выражения является необязательным (optional) значением.         
            
            
            let optionalSquare: Square? = Square(sideLength: 2.5, name: "optional square")
            let sideLength = optionalSquare?.sideLength
            
  <h2>Перечисления и структуры</h2>
  
  
  Используйте enum для создания перечисления. Как и классы и все другие именованные типы, 
  перечисления могут иметь методы, связанные с ними.
            
            enum Rank: Int {
            case ace = 1
            case two, three, four, five, six, seven, eight, nine, ten
            case jack, queen, king

            func simpleDescription() -> String {
                switch self {
                case .ace:
                    return "ace"
                case .jack:
                    return "jack"
                case .queen:
                    return "queen"
                case .king:
                    return "king"
                default:
                    return String(self.rawValue)
                }
            }
        }
        let ace = Rank.ace
        let aceRawValue = ace.rawValue        
            
            ЭКСПЕРИМЕНТ Напишите функцию, которая сравнивает два значения Rank, сравнивая их необработанные значения.
         
 По умолчанию Swift назначает необработанные значения, начинающиеся с нуля и увеличивающиеся на единицу каждый раз, 
 но вы можете изменить это поведение, явно указав значения. 
 В приведенном выше примере "ace" явно присваивается необработанное значение 1, 
 а остальные необработанные значения присваиваются по порядку. 
 Вы также можете использовать строки или числа с плавающей точкой в качестве необработанного типа перечисления. 
 Используйте свойство rawValue для доступа к необработанному значению enumeration case.
            
 
 Используйте инициализатор init? (RawValue :), чтобы создать экземпляр перечисления из необработанного значения. 
 Он возвращает либо регистр перечисления, соответствующий необработанному значению, либо nil, 
 если нет соответствующего Rank.         
            
         if let convertedRank = Rank(rawValue: 3) {
            let threeDescription = convertedRank.simpleDescription()
        }           
            
 Значения case являются фактическими значениями, а не просто способом записи их необработанных значений. 
 На самом деле, в case , когда нет необработанного значения, вам не нужно ее предоставлять.
            
                enum Suit {
                case spades, hearts, diamonds, clubs

                func simpleDescription() -> String {
                    switch self {
                    case .spades:
                        return "spades"
                    case .hearts:
                        return "hearts"
                    case .diamonds:
                        return "diamonds"
                    case .clubs:
                        return "clubs"
                    }
                }
            }
            let hearts = Suit.hearts
            let heartsDescription = hearts.simpleDescription()
            
            
            ЭКСПЕРИМЕНТ Добавьте метод color () в Suit, который возвращает  “black” для spades и clubs, 
            и вернет “red” для hearts and diamonds.
            
  Обратите внимание на два способа, в которых hearts case перечисление упоминается выше: 
  при назначении значения константе hearts  в case Suit.hearts указывается полное имя, 
  поскольку для константы не указан явный тип. 
  Внутри switch перечисления case обозначается сокращенной формой .hearts, 
  потому что значение self уже известно как иск. 
  Вы можете использовать сокращенную форму в любое время, когда тип значения уже известен.          
            
  Если перечисление имеет необработанные значения, эти значения определяются как часть объявления, 
  что означает, что каждый экземпляр конкретного случая перечисления всегда имеет одно и то же необработанное значение. 
  Другой вариант для случаев перечисления состоит в том, чтобы иметь значения, связанные с регистром - 
  эти значения определяются при создании экземпляра, и они могут различаться для каждого экземпляра регистрационного случая. 
  Вы можете думать о связанных значениях как о том, что они ведут себя как хранимые свойства экземпляра 
  enumeration case instance. 
  Например, рассмотрим случай запроса времени восхода и захода солнца с сервера. 
  Сервер либо отвечает запрошенной информацией, либо отвечает описанием того, что пошло не так.          
            
              enum ServerResponse {
                case result(String, String)
                case failure(String)
            }

            let success = ServerResponse.result("6:00 am", "8:09 pm")
            let failure = ServerResponse.failure("Out of cheese.")

            switch success {
            case let .result(sunrise, sunset):
                print("Sunrise is at \(sunrise) and sunset is at \(sunset).")
            case let .failure(message):
                print("Failure...  \(message)")
            }
            // Prints "Sunrise is at 6:00 am and sunset is at 8:09 pm."          

            
  ЭКСПЕРИМЕНТ Добавьте третий случай к ServerResponse и к switch.          
            
            
            
            





