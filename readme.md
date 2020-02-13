### шифр цезаря +
### метод простой подстановки +
### шифр виженера +
### гаммирование +
### des +
### rsa +

import itertools

file = open('message.txt', 'r')# Считываем зашифрованный текст
In = file.read()
file.close()

keyLen = int(input('Введите предполагаемую длину ключа: '))# Вводим предполагаемую длину ключа
out = ''

kolvo = 0

alphabetStr = 'абвгдеёжзийклмнопрстуфхцчшщъыьэюя'#
Инициализируем словарь русских букв
one = ['а', 'в', 'и', 'к', 'с', 'я', '-', '—', ' ']# Одиночные символы, по которым будет проходить 1 этап отбора текста
onek = 0
oney = 0
two = {}#
Инициализируем словарь для 2 этапа
glas = ['а', 'о', 'и', 'е', 'ё', 'э', 'ы', 'у', 'ю', 'я']# Глассные буквы
soglas = ['б', 'в', 'г', 'д', 'ж', 'з', 'й', 'к', 'л', 'м', 'н', 'п', 'р', 'с', 'т', 'ф', 'х', 'ц', 'ч', 'ш', 'щ']# Соглассные буквы

if keyLen == 1: #В зависимости от длины ключа генерируем всевозможные ключи
product = itertools.product(alphabetStr)
elif keyLen == 2:
  product = itertools.product(alphabetStr, alphabetStr)
elif keyLen == 3:
  product = itertools.product(alphabetStr, alphabetStr, alphabetStr)
elif keyLen == 4:
  product = itertools.product(alphabetStr, alphabetStr, alphabetStr, alphabetStr)
elif keyLen == 5:
  product = itertools.product(alphabetStr, alphabetStr, alphabetStr, alphabetStr, alphabetStr)
elif keyLen == 6:
  product = itertools.product(alphabetStr, alphabetStr, alphabetStr, alphabetStr, alphabetStr, alphabetStr)
elif keyLen == 7:
  product = itertools.product(alphabetStr, alphabetStr, alphabetStr, alphabetStr, alphabetStr, alphabetStr, alphabetStr)
else :print('Слишком длинный ключ')

for a in product: #Для всех ключей
out = ''
onek = 0
oney = 0
Key = ''.join(a)
key = ''.join(a)
two[Key] = 0
Key *= len(In) // len(Key) + 1 

for i, j in enumerate(In): #Расшифровываем текст очередным ключем
if j >= 'а'
and j <= 'я':
  out += chr((ord(j) - ord(Key[i])) % 32 + ord('а'))
elif j >= '0'
and j <= '9':
  out += chr((ord(j) - ord(Key[i])) % 10 + ord('0'))
else :
  out += j

text = out.split(' ')

for k in text: #Проверяем все одиночные символы на допустимость
onek += 1
if k in one:
  oney += 1

if (onek == oney): #Если первый этам пройден успешно, приступаем ко 2 - му
for s in range(len(out) - 1):
  if (out[s] in soglas and out[s + 1] in glas): #Если встретилась пара глассная - согласная, то записываем в словарь этапа
two[key] += 1

maximum = max(list(two.values()))# Ищем максимальное кол - во пар глассной - согласной для всех ключей
for i, j in zip(list(two.values()), list(two.keys())): #Отбираем только ключ, у которых максимальное кол - во пар глассных - согласных
if i != maximum:
  del two[j]
kolvo = len(two)# Выводим кол - во наиболее возможных комбинаций, их ключи и сами расшифрованные тексты
print('Кол-во наиболее возможных комбинаций: {}'.format(kolvo))
print('Возможные ключи: {} '.format(two))

for Key in list(two.keys()):
  out = ''
Key *= len(In) // len(Key) + 1 
for i, j in enumerate(In):
  if j >= 'а'
and j <= 'я':
  out += chr((ord(j) - ord(Key[i])) % 32 + ord('а'))
elif j >= '0'
and j <= '9':
  out += chr((ord(j) - ord(Key[i])) % 10 + ord('0'))
else :
  out += j
print(out)
