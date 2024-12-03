- Script downloads only public images from Playground.com User Profiles
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
