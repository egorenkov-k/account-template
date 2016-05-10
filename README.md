Account template
================
Класс печатной формы счета на базе HTML шаблона из 1с

Использование
-------------

### 1. Установить пакет с помощью композера

Выполнить команду в терминале

    composer require amaxlab/account-template
    
### 2. Создать класс Account

    $account = new \AmaxLab\Templates\Account(1, new DateTime());
- первый параметр "Номер счета"
- второй параметр "Дата счета"

### 3. Указать сведенья о банке

    $account->setBank('СТАРОЕ ОТДЕЛЕНИЕ СБЕРБАНКА В г. АРБАТОВА', '012345678', '30101234500000000678', '40701234567890000477');
    
### 4. Указать сведенья о продавце 

    $account->setSender('ООО Рога и копыта', '7802138119', '780201001', '109263, Г МОСКВА, УЛ МАЛЫШЕВА, Д 13, КОРП 2', '+7 (495) 6450701');
    
### 5. Указать сведенья о покупателе 

    $account->setRecipient('ИП Корейко А.И.');

### 6. Указать основание счета 

    $account->setReason('Шантаж');

### 7. Добавить позиции 

    $account->addItem('Папка "Дело А. И. Корейко"', 1, 'шт', 1000000);

### 8. Указать подписантов 

    $account->setSign('Бендер О.З.', 'Паниковский М.С.');
    
### 9. Вывести или сохранить счет 
Вывести
    $account->output();
Сохранить
    $account->save('./account.html');


Готовый пример
--------------
    <?php
    require __DIR__.'/../vendor/autoload.php';
    
    $account = new \AmaxLab\Templates\Account(1, new DateTime());
    
    $account->setBank('СТАРОЕ ОТДЕЛЕНИЕ СБЕРБАНКА В г. АРБАТОВА', '012345678', '30101234500000000678', '40701234567890000477')
        ->setSender('ООО Рога и копыта', '7802138119', '780201001', '109263, Г МОСКВА, УЛ МАЛЫШЕВА, Д 13, КОРП 2', '+7 (495) 6450701')
        ->setRecipient('ИП Корейко А.И.')
        ->setReason('Шантаж')
        ->setSign('Бендер О.З.', 'Паниковский М.С.')
        ->addItem('Гаря 12 пуд', 1, 'шт', 123.45)
        ->addItem('Папка "Дело А. И. Корейко"', 1, 'шт', 1000000);
    
    $account->save(__DIR__.'/account.html');

Результат
---------
![Account Template](http://cdn.it2k.ru/amaxlab/account-template.png)