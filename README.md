# JAV Catalog Manager V0.886, UI in Korean This Python program creates a list of JAV (Japanese Adult Video) files on
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
