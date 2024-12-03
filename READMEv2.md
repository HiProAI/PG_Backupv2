# Playground-backup
https://github.com/alexfixer/Playground-backup.git
A script to download profile public images from a Playground.

## Prerequisites

### Install Python
1. Download Python from [python.org](https://www.python.org/downloads/)
2. During installation, check "Add Python to PATH"
3. Verify installation by opening a terminal/command prompt and running:
   ```
   python --version
   pip --version
   ```

### Install Dependencies
Open a terminal/command prompt and run:
```bash
pip install requests
```

## Usage

### Basic Usage
Place the script in the folder where you want to save the images, and then open the folder in the terminal.

The script downloads data in json format, which contains available information about the images: prompt, name, dimensions, likes, generation settings, and more.

By default, the script saves both formats (png and jpeg), but you can specify only one, see the instructions below.

By default, the script saves images under the names specified in json and on the site, this will allow you to find image data by its name.

But the images in the folder will be unordered.

But if you use the `--name-by-date` option, this will add the time of its creation at the start of the image name, which will allow you to organize them.

Run:
```bash
python image-fetcher.py [USER_ID]
```
Replace `[USER_ID]` with the target user's ID or profile URL.

### Command-Line Options

| Option | Description | Example |
|--------|-------------|---------|
| `USER_ID` | Required. User ID or full profile URL | `python image-fetcher.py clc963xyc6htds601qogdmqyy` |
| `--output` | Custom output directory | `python image-fetcher.py clc963xyc6htds601qogdmqyy --output my_images` |
| `--only-png` | Download only PNG images | `python image-fetcher.py clc963xyc6htds601qogdmqyy --only-png` |
| `--only-jpeg` | Download only JPEG images | `python image-fetcher.py clc963xyc6htds601qogdmqyy --only-jpeg` |
| `--name-by-date` | Rename files to creation date | `python image-fetcher.py clc963xyc6htds601qogdmqyy --name-by-date` |
| `--name-by-date` | Rename files to creation date | `python image-fetcher.py clc963xyc6htds601qogdmqyy --start-date yyyy-mm-dd` |
| `--name-by-date` | Rename files to creation date | `python image-fetcher.py clc963xyc6htds601qogdmqyy --end-date yyyy-mm-dd` |


### Examples

1. Download all images for a user:
   ```bash
   python image-fetcher.py clc963xyc6htds601qogdmqyy
   ```

2. Download only PNG images to a specific directory:
   ```bash
   python image-fetcher.py clc963xyc6htds601qogdmqyy --output ./playground_images --only-png
   ```

3. Download images with date-based filenames:
   ```bash
   python image-fetcher.py clc963xyc6htds601qogdmqyy --name-by-date
   ```

4. Download images within a specified date range
   ```bash
   python image-fetcher.py clc963xyc6htds601qogdmqyy  --start-date 2024-01-01 --end-date 2024-03-01
   ```****

## Output Structure
- `downloaded_data/`: Default output directory
  - `png/`: PNG images
  - `jpeg/`: JPEG images
  - JSON files with image metadata

## Troubleshooting
- Ensure you have a stable internet connection
- Check that the user ID or profile URL is correct
- Verify you have write permissions in the output directory
- Check if you have enough harddisk space(up to 1.5 Gigabytes per 1000 images)

## Notes
- Script downloads only public images
- Large collections may take some time to download(up to several hours)


### Changes Version 2.0 by Hiprofile.com 
# Playground-backup
#https://github.com/alexfixer/Playground-backup.git


New Class Parameters
Added start_date and end_date parameters to the ImageFetcher class initialization
New Methods Added
Added parse_input_date method to handle date string parsing
Added is_within_date_range method to check if images fall within specified dates

Modified URL Generation
Updated the get_url method to include date filtering

Updated Fetch Logic
Modified the fetch_all method to filter images by date

New Command Line Arguments
Added two new arguments to the argument parser
Added the missing validate_user_id 
Added Progress Information
Added date range information to the console output

These changes allow you to:
Specify a date range when downloading images
Filter images based on their creation date
Download only new images by setting a start date
See which date range is being processed
Get proper validation of user IDs (both direct IDs and profile URLs)

# Download images from a specific date range
python image-fetcher_v2.py USER_ID --start-date 2024-01-01 --end-date 2024-03-01

# Download only recent images
python image-fetcher_v2.py USER_ID --start-date 2024-03-01

# Download older images
python image-fetcher_v2.py USER_ID --end-date 2024-01-01

Replace old file with the new file
