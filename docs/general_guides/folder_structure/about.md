# Folder Structure

In this section I will outline my current folder structure that works with hardlinks. I will also explain why I have chosen this structure.


## Tree

```
media (dataset)
├── download
│   ├── usenet
|   ├── syncthing
│   └── torrent
├── library
│   ├── movies
│   |     ├── anime
│   |     ├── kids
│   |     └── standard
│   ├── series
│   |     ├── anime
│   |     ├── kids
│   |     └── standard
|   └── music
```

The only dataset that is present is the media dataset, everything else is a folder created from the command line. 

I have done this because datasets are seen as separate filesystems by the operating system. This means that hardlinks cannot be created between datasets.

I did not know of this when creating my video, and had to restructure my folders, and move all of my media under a single dataset.

<br >
<br >

## Credits

Trash-Guides has a nice guide on how to setup folders for Truenas Core, and I have used this as a base for my setup.

https://trash-guides.info/Hardlinks/How-to-setup-for/TrueNAS-Core/
