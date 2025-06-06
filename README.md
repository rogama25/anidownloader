# IMPORTANT!
I'm not supporting the repo for a couple of years now, and I don't have any plans to do it. If anyone wants to continue this project, you're free to do whatever you want with the code.

---

# anidownloader

A tool to download anime chapters from AnimeFLV, built with Python.

## Installation and dependencies

To make this program work, [Mega.py](https://github.com/odwyersoftware/mega.py) and [AnimeFLV API](https://github.com/jorgeajimenezl/animeflv-api) are required. Just run the following commands in your terminal, and you'll be good to go:

```
$ pip install mega.py
$ pip install animeflv
```

After installing the dependencies, just clone the repo and run the .py file as you would do with any other .py file:

```
$ python anidownloader.py
```

## How does it work?

The program firstly asks you for a MEGA login. You can choose between two options:

- Use an anonymous temporary MEGA login. Pick this option if you don't own a MEGA account, or if you don't want to use your personal account. The only con to this choice, is that the daily download limit is 5GB, restricted by network.

- Use your own MEGA account. In case you have a MEGA PRO account (which increases the download limit), you can log in with it and download more chapters than the average user. NOTE: you will get an email when logging in. I'm not responsible of any data loss, as I'm not the creator of the library. If you have any trouble of this kind contact [O'Dwyer Software](https://github.com/odwyersoftware).

To know when the download limit has been reached, the program throws an error that looks like this:

```
File "C:\Users\YourUsername\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.10_qbz5n2kfra8p0\LocalCache\local-packages\Python310\site-packages\mega\mega.py", line 731, in _download_file
    block = chunk[i:i + 16]
UnboundLocalError: local variable 'i' referenced before assignment
```

After that you will find a menu, where you can choose between 4 options:

0. "Buscar animes": It will ask for a search term, and print all matching results found in AnimeFLV.

1. "Ver la información de un anime": It does the same as option 0, but you can pick an anime to watch more info about it. Here's an example.

   ```
   Bienvenido a Anidownloader
   ------------------------------
   (0) - Buscar animes
   (1) - Ver la información de un anime
   (2) - Descargar capítulos de un anime
   (3) - Finalizar script
   
   Escoja una opción: 2
   Introduzca el nombre del anime: Shingeki no Kyojin
   Se han encontrado 11 resultados
   
   1.Shingeki no Kyojin: Kuinaki Sentaku
   
   2.Shingeki no Kyojin OVA
   
   3.Shingeki no Kyojin: The Final Season
   
   4.Shingeki no Kyojin Season 3
   
   5.Shingeki no Kyojin
   
   6.Shingeki no Kyojin Movie 1: Guren no Yumiya
   
   7.Shingeki no Kyojin: The Final Season Part 2
   
   8.Shingeki no Kyojin Season 3 Part 2
   
   9.Shingeki no Kyojin: The Final Season
   
   10.Shingeki no Kyojin: Chimi Kyara Gekijou - Tondeke! Kunren Heidan
   
   11.Shingeki no Kyojin: Lost Girls
   
   Escoja una de las opciones mostradas: 4
   Título: Shingeki no Kyojin Season 3
   AnimeFLV id: anime/shingeki-no-kyojin-season-3
   Tipo: Anime
   Sinopsis: Tercera temporada de Shingeki no Kyojin
   Episodios: 12
   Puntuación: 4.6 / 5
   ```

2. "Descargar capítulos de un anime": It will ask you to search for an anime, and after you pick it, you will be asked to choose between downloading all chapters, or downloading a single chapter. After that, the desired episodes will start downloading in the folder where you have anidownloader.py stored.

3. "Finalizar script": Closes the program.

## Common errors and how to solve them

You might find some errors when using the program. These do not come from it, but from the APIs and libraries used. Here's a little guide on how to solve them:

- PermissionError [WinError 32]: You're most likely to get this error in the downloadChapter function. To fix this, head over to MegaAPI's mega.py file, go to lines 745 and 746 and remove a tab from them. That should do the fix.

- Parser error in __ getAnimeEpisodesInfo __(): You will get this error on line 111 of anidownloader.py. To fix it you need to change lines 180 and 181 of AnimeFLV API. Head over to AnimeFLV API's init.py file replace those lines with the following:

  ```
  "title": soup.select_one('body div.Wrapper div.Body div div.Ficha.fchlt div.Container h1.Title').string,
  "poster": soup.find("meta", property="og:image")['content'],
  ```

- UnboundLocalError - local variable 'i' referenced before assignment: You've reached the 5GB daily download limit. There's nothing you can do about it for now, maybe using a VPN will work, but I have no idea.

- "No se ha encontrado ningún resultado, volviendo al menú principal": You will get this when the search term you entered hasn't matched with any of AnimeFLV's anime names. 

  There are cases where this pops up even when the search team you entered is correct. In this last case, trying to search multiple times or waiting some seconds will fix it. If this doesn't fix it, restart the program until it works.

  I'm sorry but it's the only fix I've found for now, there must be some issue with the AnimeFLV API.

- "No se han encontrado enlaces de MEGA para este capítulo": It means that the chapter cannot be downloaded, as a matching MEGA link for the chapter wasn't found. This sometimes happens even when there's a link (it happened to me while testing downloading Shingeki no Kyokin Season 4 Part 2 Episode 12).

  I still haven't found a solution to this yet, the only thing you can do for now is go to AnimeFLV and look for it manually.

- mega.errors.RequestError: ENOENT, Object (typically, node or user) not found: This happens when the login data (email or password) is wrong. Execute the program again and type a valid account. In case the error persists, try recovering your account on the official MEGA page.

## Latest updates

These are the latest aditions to anidownloader:

- (Added - 17/07/2022) Log in with your own MEGA account, so if you have a Pro MEGA account you can surpass the 5GB download limit.
- (Added - 22/07/2022) Make the download path relative, so there's no need to change it for every different user.
- (Added - 22/07/2022) Create automatically a folder for every different anime downloaded, so you can have everything organized without having to do anything manually.

## Planned future features

As for now, I'm planning to add these features to the program:

- Option to download groups of chapters (f/e, download from chapter 4 to 20).
- Language selector.
- More file providers, like Zippyshare.
- Graphical user interface to make anidownloader more intuitive to use.

## License

Licensed under the MIT license.
