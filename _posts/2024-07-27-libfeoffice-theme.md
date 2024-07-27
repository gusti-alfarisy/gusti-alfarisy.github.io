---
title: How to Customize LibreOffice with GTK Themes on Ubuntu/Linux
date: 2024-07-27
background: "https://ubunlog.com/wp-content/uploads/2016/11/libreoffice-768x370.jpg.webp"

author: Gusti Ahmad Fanshuri Alfarisy
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
#tags: [Data, Shared tag]
comments: true
---

# How to Customize LibreOffice with GTK Themes on Ubuntu/Linux

Do you feel weird using libreoffice in dark mode theme? Same here! I really enjoying using Ubuntu Linux with dark mode. But, it seems not fit for few applications like LibreOffice. I prefer the light mode over the dark one. Here is step-by-step guide on how you can fix it so that whenever you run LibreOffice, it will automatically run in light mode.

You can open the terminal first. Then, open the files manager or nautilus in `/usr/share/applications/` directory using below command:

``` nautilus /usr/share/applications/ ```

Next, open the other terminal and using the same command to open `~/.local/share/applications/` directory using below command:

``` nautilus ~/.local/share/applications/ ```

With the dirrectory `~/.local/share/applications/`, search the files with prefix "libre" then copy all the files to the other directory (`/usr/share/applications/`). The list of files that should be copied are:

- libreoffice-startcenter.desktop
- libreoffice-writer.desktop
- libreoffice-calc.desktop
- libreoffice-impress.desktop
- libreoffice-draw.desktop

Having all files in `/usr/share/applications/`, edit the libreoffice-startcenter.desktop file using text editor and find the `Exec` term, you will find like this: `Exec=libreoffice %U`. Change the command by adding the GTK theme:

``` Exec=env GTK_THEME=Default libreoffice %U ```

Save and close the files, and viola! The LibreOffice Start Centre now becomes light mode in default, you can start any applications and will automatically using light theme.

In case you want to start the light mode with specific applications, let say LibreOfficeWriter. You also use the same command. Open `libreoffice-writer.desktop` file, then find the `Exec` command. In this time, there are two `Exec` command. Please make sure you change both of them to:

``` Exec=env GTK_THEME=Default libreoffice %U ```

Viola!.. Done!

For other apps like Calc, Impress, Draw, etc. You just follow the step above that makes the Writer use the light theme as default.