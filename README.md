# MODIS data grabber
This script download MODIS product. It is part of a framework allowing to fetch and process MODIS Atmosphere products. This is a modification of our original MODIS data grabber. This is done, when the server was migrated from FTP to HTTPS.

The repository is separated for MYD and MOD time satellite captures. Please run the scripts separately for both MYD and MOD time captures.

Please contact [S. Manandhar](SHILPA005@e.ntu.edu.sg) or [S. Dev](https://soumyabrata.github.io/) for any queries. 

```
Manual:
        1. Folder structure: this script should be in code/ModisGrabber/. Then you must create a directory named _data/
        in the code/ directory. This script will download the products there. Once a download is finished, you should
        move the data from the _data/ folder to the data/ one, so you can use them, and so that the grabber has a empty
        directory for it next download.
            Final stucture:
                code/
                     _data/          # Use for download only.
                     data/           # Data already downloaded, to be use with the other scripts.
                     ModisGrabber/   # Location of this script.

       2. Once this is done, read the PARAMETERS section. Read the comments for the syntax, and modify them as you
       wish.
       3. Run the script. What it does,
            For each date**:
                 * Create a directory: _data/data-{DATE}/. If the directory exist, it *wipes* it !!!!!
                 * Download geolocalisation dataset. Parse the file to find when AQUA and/or TERRA was above the bounding box.
                 * Then select the right products, download them.
                 * Once the download of all the product is done, it put a flag. A flag is a file into the directory
                     _data/data-{DATE}/.
                        If this file name is FAILURE, do not use what was downloaded and re-launch the grabber
                            for this day.
                        If this file name is SUCCESS, you can move the folder (i.e day) to data/, and use the products
                        If there is no file, then probably the download isn't finished yet.
                   The file contains a timestamp, along the reason of the failure if it didn't work, along with the name
                   of the products concerned.
```
