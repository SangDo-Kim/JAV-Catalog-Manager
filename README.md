# JAV Catalog Manager V1.51, UI in Korean
This Python program creates a list of JAV (Japanese Adult Video) files on local hard drives.
It allows users to search for video files, play them, and retrieve JAV title information (poster images and star names)
from the Internet.
JAV 카탈로그 매니저, 야동 관리 프로그램
이 Python 프로그램은 로컬 하드 드라이브에 있는 JAV(일본 성인 비디오) 파일 목록을 생성합니다.
사용자는 영상 검색, 영상 재생, 인터넷에서 JAV 타이틀 정보(포스터 이미지 및 출연자 이름)를 가져올 수 있습니다.

V0.7
- Initial creation_

V0.73
- Upgraded: Folder scanning feature
- Added: Sorting feature

V0.74
- Added: Event logger for logging errors and process statuses

V0.75
- Upgraded: Enhanced search feature with OR search using the | operator, and added exclusion conditions

V0.80
- Added: Ability to search for JAV star names online

V0.81
- Upgraded: Reduced loading time by implementing staggered thumbnail image loading

V0.82
- Bugfix: Staggered thumbnail images did not fully load

V0.83
- Upgraded: Progress is now shown in the file scan dialog widget
- Changed: After file scan or internet search, data is reloaded from scratch

V0.84
- Added: Users can select a data card by clicking or using the w, a, s, d keys
- Added: Data cards are now selectable
- Users can select a data card by clicking or using the w, a, s, d keys
- Press the space bar to play the video
- Selection is saved and reinstated when the program is restarted

V0.85
- Added: Rating system allowing users to give 0 to 5 stars to each video, with sorting based on ratings
- Added: Ability to delete a video using the Del key

V0.86
- Fixed: Issue with adding production codes to prod_db during file scan

V0.871
- Fixed: Rating-related error

V0.872
- Changed: File settings dialog box now includes the file scan feature

V0.882
- Added: Customizable displayed titles
- Added: Tabs for movie, star, and genre pages (genre page not yet implemented)
- Added: Support for Caribbeancom-100000-000
- Added: Auto-generation of prod_code for videos without a prod_code in the file name
- Fixed: Inconsistent application of rating changes

V0.883
- Fixed: Issue with some images (RGBA) causing scan poster function to stop

V0.884
- Enhanced: Shortened data card loading time and reduced memory usage

V0.885
- Added: Option for users to input strings to exclude from web scraping during internet search
- Fixed: Bugs related to data card loading and enhanced performance

V0.886
- Enhanced: Data cards are now displayed from the top to reduce flickering
- Fixed: Title settings not applied when searching and displaying new data cards
- Fixed: Prevent the program initialize on genre tab. Genre tab is not implemented.

V1.0
- Added: Genre view
- Added: File name change feature
- Fixed: When initial program run, folder setting stopped in the middle of run.

V1.01
- Fixed: File name change was not done correctly for ZZZ prod_code.

V1.1
- Added: Data cards are now set to landscape. Set in [Settings and shortcut].
- Added: Instead of default media player, users can now specify one.

V1.11
- Added: Theme selection: Beige, Dark

V1.12
- Added: Sage's Moment - Press the Z key to play soothing music (supports web URL or local file path).
- Changed: Top left logo and title color updated to a grayish shade to ensure visibility in both light and dark themes.

V1.2
- Enhanced: Tab switching is now significantly faster. Each tab has its own dedicated data sets and attributes,
    eliminating the need for reallocation.
- Added: New theme, Black.

V1.21
- Changed: Refactored codes to handle tab related attributes with dictionaries.

V1.3
- Added: Deleted movie information is now preserved and can be shown according to user settings.
- Fixed: Files without extension were falsely recognized as movie files when Refresh files.

V1.31
- Added: Random play button

V1.32
- Fixed: JAV star names are not searched due to recent policy change in Google UK.
    Now users need to log in Google.com and certify adult to search, then run this program to get star names.

V1.4
- Added: Page System for Optimized Data Card Loading
    Implemented a page system to load a limited number of data cards at a time,
    instead of loading all cards at once.
    This improvement significantly enhances performance, especially when handling large datasets with hundreds
    of data cards.
    UI Enhancements in JCM_main_ui.py: Users can now navigate through pages to view additional data cards:
    QLabel: label_page_total_movie displays the total number of pages.
    QLineEdit: lineEdit_page_current_movie allows users to type in a page number.
    QPushButton: pushButton_page_next_movie and pushButton_page_prev_movie enable navigation to the next and
    previous pages, respectively.
    These same UI components exist for the star and genre sections, with the respective _star and _genre postfixes
    (e.g., label_page_total_star, pushButton_page_next_star, etc.).
    Related Configuration: The page_size variable in JCM_config.py controls the number of data cards displayed per page.

V1.41
- Added: SVG video format is included.

V1.42
- Fixed: During poster request from web, the program now can handle when remote website blocks (ConnectionResetError 10054)

V1.5
- Fixed: Star name web search was still failed. Changed from simple HTTP requests to Selenium with Chrome.

V1.51
- Fixed: Updated poster scraping sources to active ones.
- Changed: Show module number on success instead of at start.
  
Important files:
JCM_main.py
    This module defines the MainWindow class, which serves as the main application window for managing and displaying
    information about movies, stars, and genres. The data is loaded from various databases, processed,
    and then displayed using a grid layout of data cards.

JCM_main_ui.py - PySide6 auto-generated UI elements.
JCM_resources_rc.py - PySide6 auto-generated resource file for icons and images for the program.
JCM_config.py - class JCMConfig. Handles configuration data.
data_card.py - class DataCard(QWidget). Data cards which are a series of widgets with titles, pictures, buttons.
search_internet.py - class InternetSearch(QDialog, Ui_Dialog). Search internet and get Poster image and make thumbnails,
    and also get star name using given JAV product code.


Important attributes:
    merged_df (pd.DataFrame): Data frame containing information about movies from file_db, prod_db, and others.
        star_df and genre_df are concatenated to merged_df.
    star_df (pd.DataFrame): Data frame containing information about stars, merged from star_db and prod_star_db.
    genre_df (pd.DataFrame): Data frame containing information about genres, merged from genre_db and prod_genre_db.

    display_df_dict (dict): Dictionary containing data frames for displaying information.
        Example usage:
            display_df_dict[Cons.movie]
            display_df_dict[self.tab]
            Here, self.tab can be "movie", "star" or "genre", automatically assigned on tab switch.

    data_cards (dict): Dictionary to hold the created data cards.
        Example usage:
            self.data_cards[index_label] = DataCard_instance
        Here, index_label is an integer unified throughout merged_df, display_df_dict,
            and most of DataFrames in MainWindow.

    grid_map_dict (dict): Dictionary to hold grid maps for movies, stars, and genres.
        Example usage:
            self.grid_map_dict[Cons.movie][(row_number, column)] = DataCard_instance.index

    tab (str): Current tab (movie, star, genre).

Related DataFrames (each have its independent modules):
    file_db.df: unique column: full_file_path, join column: prod_code
    prod_db.df: unique column: prod_code
    star_db.df: unique column: star_id
    prod_star_db.df: Join table for prod_db and star_db.
    genre_db.df: unique column: genre_id
    prod_genre_db.df: Join table for prod_db and genre_db
* Note that index labels of the xxxx_db.df are different from the index labels of merged_df, display_df, data_cards
    and most of DataFrames in MainWindow.
