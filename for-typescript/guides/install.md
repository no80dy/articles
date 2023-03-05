### Установка TypeScript на Debian

#### Установка nmp
Для того чтобы установить TypeScript, нам нужно поставить npm (Node Package Manager). Пропишем следующие команды:
```bash
sudo apt install npm
```

#### Установка TypeScript
После того, как мы поставили npm, можно приступить к установке TypeScript:
```bash
sudo nmp install -g typescript
```

#### Создание проекта TypeScript
После установки всех необходимых компонентов, можно приступить к созданию проекта. Для этого в папку нужно добавить файл с типом `.ts`. Данный файл хранит код 
языка TypeScript и перекомпилируется в формат `.js`. Для компиляции TypeScript кода применим следующую команду:
```bash
tsc {file name}.ts
```
После выполнения компиляции в папке появится файл с кодом на JavaScript.