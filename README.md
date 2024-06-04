# JAV Catalog Manager V0.84, UI in Korean
This Python program makes a list of JAV (Japanese Adult Video) files on local hard drives.
It lets users search video files, play them, and get JAV title information
(poster images and star name) from the Internet.
이 Python 프로그램은 로컬 하드 드라이브에 있는 JAV(일본 성인 비디오) 파일의 목록을 만듭니다.
사용자는 영상 검색, 영상 재생, 인터넷에서 JAV 타이틀 정보(포스터 이미지 및 출연자 정보)를 가져올 수 있습니다.

V0.7
- Initial creation

V0.73
- Upgraded: Scan folder feature
- Added: Sort feature

V0.74
- Added: Event logger which can log errors or process status.

V0.75
- Upgraded: Search feature now allows | operator for OR search. And excluding condition is added.

V0.80
- Added: Search for JAV star name from web.

V0.81
- Upgraded: Shortened the loading time by implementing staggered thumbnail image loading.

V0.82
- Bugfix: Staggered thumbnail images did not load fully.

V0.83
- Added: JAV_db_utils module
- Upgraded: In scan files dialog widget, it now shows the progress.
- Changed: After scan file or internet search, now reload data from scratch.

V0.84
- Added: User can select a data card by clicking or w, a, s, d key.
- Added: Data card now selectable.
    User can select a data card by clicking or using w, a, s, d keys.
    Press the space bar to play the video.
    The selection is saved and reinstated when the program starts next time.
