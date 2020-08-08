# `pip` Libriries

## pip

- They can be stored on the Python Package Index (PyPI). Here are some useful commands.
- If both python 3 and python 2 is on the system, then running `pip` will update your library for python 2 while `pip3` will update your library for python 3.
- `pip install <packagename>` install a package
- `pip install --upgrade <packagename>` update a package
- `pip install -r requirements.txt` install packages according the `requirements.txt`
- `pip uninstall <packagename>` uninstall a package
- `pip search <keyword>` search for a package
- `pip list` list packages
- `pip freeze` output package info file
  - `pip freeze >requirement.txt` output package info file as txt file.
- `pip install -U pip` update pip

### Postgres

- It provide the required driver to connect to a `Postgres` database.
- Run `pip install psycopg2`
- Example Usage

```py
#Import the python driver for PostgreSQL
import psycopg2

#Create a connection credentials to the PostgreSQL database
try:
    connection = psycopg2.connect(
        user = "postgres",
        password = "1234",
        host = "localhost",
        port = "5432",
        database = "demo"
    )

    #Create a cursor connection object to a PostgreSQL instance and print the connection properties.
    cursor = connection.cursor()
    print(connection.get_dsn_parameters(),"\n")

    #Display the PostgreSQL version installed
    cursor.execute("SELECT version();")
    record = cursor.fetchone()
    print("You are connected into the - " record,"\n")

    #Get the column name of a table inside the database and put some values
    pg_insert = """ INSERT INTO book (id, author, isbn, title, date_published)
                VALUES (%s,%s,%s,%s,%s)"""

    inserted_values = (1, 'Layla Nowiztki', '789-1-46-268414-1', 'How to become a professional programmer', 'January 25 2011')

    #Execute the pg_insert SQL string
    cursor.execute(pg_insert, inserted_values)

    #Commit transaction and prints the result successfully
    connection.commit()
    count = cursor.rowcount
    print (count, "Successfully inserted")


#Handle the error throws by the command that is useful when using python while working with PostgreSQL
except(Exception, psycopg2.Error) as error:
    print("Error connecting to PostgreSQL database", error)
    connection = None

#Close the database connection
finally:
    if(connection != None):
        cursor.close()
        connection.close()
        print("PostgreSQL connection is now closed")
```

- `inserted_values` has to be a tuple, even if it has only one parameter. For example, use `(1,)`.

## pyttsx3

- Pyttsx is completely offline and works seemlesly and has multiple tts-engine support.
- By default, the pyttsx3 library loads the best driver available in an operating system: nsss on Mac, sapi5 on Windows and espeak on Linux and any other platform.

### Usage

- pick voice
  ```py
  import pyttsx3
  engine = pyttsx3.init()
  voices = engine.getProperty('voices')
  for voice in voices:
    engine.setProperty('voice', voice.id)
    engine.say('Nice to meet you!')
    engine.runAndWait()
  ```
- female voice pick `voices[10]`, `voices[17]`

## gTTS

- gTTS (Google Text-to-Speech)
- It requires internet connection.
- It writes spoken mp3 data to a file, a file-like object (bytestring) for further audio manipulation, or stdout. Or simply pre-generate Google Translate TTS request URLs to feed to an external program.

## virtualenv

- run `pip` with `sudo` will install the module globally.
- `pip install virtualenv`
- In the project folder run `virtualenv <env_name>` create new env
- `source <env_name>/bin/activate` activate new env
- `deactivate` leave an env
