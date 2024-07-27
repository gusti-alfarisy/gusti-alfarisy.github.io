---
title: How to Customize LibreOffice with GTK Themes on Ubuntu/Linux
date: 2024-07-27
background: "https://ubunlog.com/wp-content/uploads/2016/11/libreoffice-768x370.jpg.webp"

author: Gusti Ahmad Fanshuri Alfarisy
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
tags: [Linux, Ubuntu, LibreOffice]
comments: true
---

# How to Customize LibreOffice with GTK Themes on Ubuntu/Linux with Light Theme
Do you find it awkward to use LibreOffice in dark mode? Same here! I really enjoy using Ubuntu Linux with dark mode, but it doesn’t seem to fit well with certain applications like LibreOffice. I prefer the light mode for LibreOffice. Here is a step-by-step guide on how you can ensure LibreOffice always runs in light mode.

First, open the terminal. Then, open the file manager (Nautilus) in the `/usr/share/applications/` directory using the command below:

```sh
nautilus /usr/share/applications/
```

Next, open another terminal and use the same command to open the `~/.local/share/applications/` directory:

```sh
nautilus ~/.local/share/applications/ 
```

In the `~/.local/share/applications/` directory, search for files with the prefix "libre" and copy all the files to the other directory (`/usr/share/applications/`). The list of files that should be copied are:

- libreoffice-startcenter.desktop
- libreoffice-writer.desktop
- libreoffice-calc.desktop
- libreoffice-impress.desktop
- libreoffice-draw.desktop

Once all the files are in `/usr/share/applications/`, edit the libreoffice-startcenter.desktop file using a text editor and find the `Exec` term. You will see something like this: `Exec=libreoffice %U`. Change the command by adding the GTK theme:

```sh
Exec=env GTK_THEME=Default libreoffice %U 
```

Save and close the file, and voila! The LibreOffice Start Center will now default to light mode. You can start any application, and it will automatically use the light theme.

If you want to start in light mode with a specific application, such as LibreOffice Writer, you can use the same command. Open the `libreoffice-writer.desktop` file and find the `Exec` command. This time, there are two Exec commands. Make sure you change both of them to:

```sh
Exec=env GTK_THEME=Default libreoffice %U 
```

Viola!.. Done!

For other applications like Calc, Impress, Draw, etc., just follow the same steps to ensure they use the light theme by default.