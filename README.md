# Whatchat
Архипов Даниил Олегович
Имя тимлида Даниил;

### Описание выбранной идеи решения

В данной реализации разработано приложение для чата, которое поддерживает как публичные, так и личные сообщения. Основная цель — предоставить пользователям возможность обмениваться сообщениями в открытых чатах и личных переписках. Каждое сообщение сохраняется как у отправителя, так и у получателя, что позволяет обеим сторонам видеть историю общения.

Ключевые особенности решения включают:
- Регистрация и аутентификация пользователей.
- Возможность отправки как публичных сообщений (всем пользователям), так и личных сообщений (конкретным пользователям).
- Хранение всех сообщений, что позволяет пользователям просматривать историю переписки.
- Удобный интерфейс для взаимодействия с приложением, включая возможность выбора получателя сообщения.

Таким образом, приложение предлагает интуитивно понятный способ общения и эффективное управление сообщениями.

### Описание пользовательских типов и функций в проекте

#### 1. Класс `Message`

- **Поля:**
  - `string sender`: логин отправителя сообщения.
  - `string recipient`: логин получателя сообщения (может быть пустым для публичных сообщений).
  - `string content`: текст сообщения.

- **Конструктор:**
  - `Message(const string& sender, const string& content, const string& recipient = "")`: инициализирует объект сообщения с заданным отправителем, содержимым и (опционально) получателем.

#### 2. Класс `User `

- **Поля:**
  - `string login`: логин пользователя.
  - `string password`: пароль пользователя.
  - `string name`: имя пользователя.

- **Конструкторы:**
  - `User ()`: конструктор по умолчанию, инициализирующий пустие значения.
  - `User (string login, string password, string name)`: инициализирует объект пользователя с заданным логином, паролем и именем.

- **Методы:**
  - `void sendMessage(const string& message, const string& recipient = "") const`: отправляет сообщение, выводя его на экран.

#### 3. Класс `Chat`

- **Поля:**
  - `map<string, User> users`: хранит зарегистрированных пользователей, где ключ — логин, а значение — объект `User `.
  - `vector<string> onlineUsers`: список пользователей, которые в данный момент онлайн.
  - `vector<Message> publicMessages`: хранит публичные сообщения, отправленные всеми пользователями.
  - `map<string, vector<Message>> privateMessages`: хранит личные сообщения для каждого пользователя, где ключ — логин пользователя, а значение — вектор сообщений.

- **Методы:**
  - `bool registerUser (const string& login, const string& password, const string& name)`: регистрирует нового пользователя. Возвращает `true`, если регистрация успешна, и `false`, если логин уже занят.
  - `bool loginUser (const string& login, const string& password)`: выполняет вход пользователя в систему. Возвращает `true`, если вход успешен, и `false`, если логин или пароль неверны.
  - `void logoutUser (const string& login)`: выходит пользователя из системы.
  - `void sendMessage(const string& senderLogin, const string& message, const string& recipient = "")`: отправляет сообщение. Если получатель не указан, сообщение считается публичным, иначе — личным.
  - `void listUsers(string login, int count) const`: выводит список всех зарегистрированных пользователей, исключая текущего пользователя.
  - `void viewMessages(const string& login) const`: отображает все сообщения (публичные и личные) для данного пользователя.

### Заключение

Данная структура и логика приложения позволяют создать функциональный чат, который поддерживает как публичные, так и личные сообщения. Пользователи могут легко регистрироваться, входить в систему, отправлять сообщения и просматривать историю переписки, что делает приложение удобным и эффективным для общения.
