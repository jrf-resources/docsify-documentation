# How to add a desktop entry on Elementary OS
> Often with less supported appps you may find the need to create a custom `.desktop` entry for an app you are trying to run through the user interface.  Here is a guide on how to do so for Elementary OS, using [InvoiceNinja](https://www.invoiceninja.com/) as an example.

## Create contents of .desktop file
Paste the following contents into a text editor and adjust it to your needs:
```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Invoice Ninja
Comment=Accounting software
Exec=/home/jesse/apps/invoice-ninja-linux-x64/invoice-ninja
Icon=/home/jesse/apps/invoice-ninja-linux-x64/resources/app/icon.png
Categories=Web
Terminal=false
```
| Field to Change  |  Description |
| ------------ | ------------- |
| Name         |  Name of the app you are adding the desktop entry for    |
| Comment   | A description of the app |
| Exec            | The path to the app executable. No spaces allowed here so escape them with `\` |
| Icon            | The path to the app icon. No spaces allowed here so escape them with `\` |
| Categories | Comma separated list of category names |

## Save the .desktop file
After you are finished adjusting, you can either save it to the root folder or your home directory.  Both commands are below:
```bash
sudo nano /usr/share/applications/invoiceninja.desktop
# OR
nano ~/.local/share/applications/invoiceninja.desktop
```
Adjust the filename to your needs and then paste in the contents from the text editor.  `ctrl + o` to save and `ctrl+x` to exit.
## Make the .desktop file executable
Next we need to make the file executable by the system.  Execute one of these below, depending on which command you ran above.
```bash
sudo chmod +x /usr/share/applications/invoiceninja.desktop
# OR
chmod +x ~/.local/share/applications/invoiceninja.desktop
```
That's it, your app should now appear in the system menu!