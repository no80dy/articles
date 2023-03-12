### Установка компонентов Visual Studio 2022 на Win10

#### Разбираемся с местоположением
Для того, чтобы установить компоненты с конкретным названием, например `Microsoft.VisualStudio.Workload.NativeDesktop`, потребуется информация о расположении установщика 
(Visual Studio Installer) и о расположении места, где находятся установленные компоненты нашей IDE. В моем случае, установщик был расположен на диске 
`C:\Program Files (x86)\Microsoft Visual Studio\Installers\`, а дирректория с установленной IDE распологалась в `D:\VisualStusio\IDE`. Однако, если вы не знаете, 
где находятся установленные вами компоненты, воспользуйтесь терминалом `PowerShell` и пропишите в нем следующие команды:
```powershell
PS C:\something> cd C:\
PS C:\> Get-Childitem -recurse -filter "vs_*.exe"
```
Вывод команды будет примерно таким в моем случае:
```powershell
Каталог: C:\Program Files (x86)\Microsoft Visual Studio\Installer


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        06.03.2023     22:28         202160 vs_installer.exe
-a----        06.03.2023     22:28          31688 vs_installer.windows.exe
-a----        06.03.2023     22:28         202160 vs_installershell.exe
-a----        06.03.2023     22:28         252848 vs_layout.exe
```
Итак, мы нашли местоположение нашего установщика, однако, где находится сам IDE. Тут мы воспользуемся самой программой Visual Studio Installer и перейдем в расположение установки:

![image](https://user-images.githubusercontent.com/127035207/223219032-0fef0ebc-3514-494d-ab90-0ad89e238e27.png)

Тут то мы и находим местоположение Visual Studio.
> NOTE: не забывайте открывать PowerShell в режиме прав администратора, иначе могут возникнуть неожиданные исключения.

#### Установка с помощью PowerShell
Для установки всех пакетов нам также потребуется PowerShell. Для того, чтобы установить нужную нам программу, нужно прописать в терминале следующую команду:
```powershell
PS C:\Program Files (x86)\Microsoft Visual Studio\Installer> .\vs_installer.exe modify --installPath "D:\VisualStudio\IDE" --add Microsoft.VisualStudio.Workload.NativeDesktop --add Microsoft.VisualStudio.Component.VC.ATLMFC --includeRecommended
```
В примере выше мы устанавливаем два пакета: `Microsoft.VisualStudio.Workload.NativeDesktop` и  `Microsoft.VisualStudio.Component.VC.ATLMFC`, а перед этим указываем расположение установщика и самой IDE соответственно.
Далее нас перекидывает в графический установщик. Осталось только нажать на кнопку изменить.
