# JAV Catalog Manager V1.1, UI in Korean This Python program creates a list of JAV (Japanese Adult Video) files on
local hard drives. It allows users to search for video files, play them, and retrieve JAV title information (poster
images and star names) from the Internet.
이 Python 프로그램은 로컬 하드 드라이브에 있는 JAV(일본 성인 비디오) 파일 목록을 생성합니다. 사용자는 영상 검색,
영상 재생, 인터넷에서 JAV 타이틀 정보(포스터 이미지 및 출연자 이름)를 가져올 수 있습니다.

V0.7
- Initial creation

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

JCM_main.py, class MainWindow attributes:
    merged_df (pd.DataFrame): Data frame containing information about movies from file_db, prod_db, and others.
        star_df and genre_df are concatenated to merged_df.
    star_df (pd.DataFrame): Data frame containing information about stars, merged from star_db and prod_star_db.
    genre_df (pd.DataFrame): Data frame containing information about genres, merged from genre_db and prod_genre_db.
    display_df (pd.DataFrame): Subset of merged_df used for displaying the data cards.
    display_prev_df (pd.DataFrame): Data frame to track the previous state of display_df for detecting changes.
    display_diff_df (pd.DataFrame): Data frame to track the differences between display_df and display_prev_df.

    data_cards (dict): Dictionary to hold the created data cards.
        self.data_cards[index] = DataCard instance.
        Here, index is an integer unified throughout merged_df, display_df, and most of DataFrames.
    grid_map (dict): Dictionary to hold column and row info of currently displayed data cards.
        self.grid_map[(row_number, column)] = DataCard_instance.index
    tab (str): Current tab (movie, star, genre).

    Related DataFrames (each have its independent modules):
    file_db.df: unique column: full_file_path, join column: prod_code
    prod_db.df: unique column: prod_code
    star_db.df: unique column: star_id
    prod_star_db.df: Join table for prod_db and star_db.
    genre_db.df: unique column: genre_id
    prod_genre_db.df: Join table for prod_db and genre_db
    * Note that index of the xxxx_db.df are different from the index of merged_df, display_df, data_cards and so on.
