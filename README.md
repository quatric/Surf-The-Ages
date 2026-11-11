# Surf The Ages

Surf The Ages from World Book 2013 for Mac (MacKiev): an imagined World Wide
Web of the past, with sites, news and shops for each period from ancient
times to the twentieth century. The app showed it in its own browser. This
is the same content as a folder of plain HTML that opens in any web browser.

Open `index.htm`.

## How it was extracted

The content ships in `2013 World Book.app/Contents/Resources/Surf.book`:

- `Archive/ArticlePath.idx` holds every page's path.
- `DataIndex.idx` says where each page's data is, either a zlib stream or a stored file in `Archive/ArticleArchive.zip`, or a file in the bundle's `Pictures/`, `Sounds/` or `Movies/`.

`tools/surf_extract.py` in the World Book Universal 2 project reads these and
writes each file out. On the way it does three things:

- It turns `stm://SurfTheAges/` links into relative links.
- It turns links to World Book articles (`stm://WB/...`), which only the app can show, into plain text.
- It lowercases relative file names to match the archive, since the app's protocol ignored case.
- It stops wide backgrounds tiling. The app showed the pages in a window about 1068 × 731, so a wide background never repeated across it. A scene behind a page is shown once, and a strip with a border down its left edge repeats only downwards, with the rest of the page in the strip's own colour. Small textures still tile.

Three leftover `.tmp` entries point to files that never shipped and are
missing. A few dozen links were already dead in the original content.

The pages are © World Book, Inc. and Software MacKiev.
