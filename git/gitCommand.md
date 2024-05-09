# 로컬이랑 서버랑 파일경로가 다를 때 로컬에서 경로를 수정해야하는데 git에서 더이상 추적하지 않도록 하는법
gitignore는 아예 추적을 안해서 push할때 해당 프로그램이 빠지는데 이게 git에서는 현재 버전이 포함되면서 이후 버전

보안키패드 로컬이랑 특정환경 서버 파일 서버 경로 매번 바꿔주지 않도록 하려면,
git bash 터미널 에서 아래 명령어 치고 아래 두 ini파일은 각자 로컬 경로에 맞게 두시고 사용하시면 됩니다.
git update-index --skip-worktree src/main/resources/raon_config/config.ini
git update-index --skip-worktree src/main/resources/raon_config/transkey_license.ini 