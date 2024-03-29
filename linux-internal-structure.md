# 파일 시스템
1. 운영 체제에서는 커널 이미지, 시스템 실행과 관련된 시스템 파일 그리고 유틸리티 파일 등을 제공한다.

2. 사용자의 데이터의 저장을 위해서 사용 됨.

3. 파일 시스템을 통해 이러한 파일들을 관리된다.

4. 파일 시스템은 파일의 저장, 삭제 읽기 등의 파일 관리 기능과 파일에 대한 접근 제어 기능을 제공 

5. 윈도우에서는 FAT32, NTFS와 같은 파일 시스템을 제공하고 리눅스 에서는 EXT2, EXT3 와 같은 파일 시스템을 제공

6. 디렉터리 안에 디렉터리를 저장할 수 있는 구조

7. 루트 디렉터리 : 장치의 메인 디렉터리
 
    - 여러 장치(하드 디스크)를 사용하게 되면 루트 디렉터리 구분에 문제가 생긴다.

    - MS 윈도우에서 분리형 루트라 불리는 방식으로 이를 해결한다.

    - 유닉스 계열에서는 통합형 파일 시스템을 사용한다.

## 가상 파일시스템(VFS)

- 유닉스는 디스크, 터미널, 네트워크 카드 등 **모든 주변 장치들을 파일로 취급**한다. 
- 따라서 디스크상의 파일 시스템 외에도 다양한 기능의 특수 파일 시스템이 존재하는데 리눅스 에서는 이러한 다양한 파일 시스템들을 하나의 파일 시스템 처럼 사용할 수 있게 가상 파일 시스템이라는 구조를 사용 한다.
![image](https://velog.velcdn.com/images/myway00/post/01c32b94-a0ec-4672-bf17-76a579acf464/image.png)
 
1. 리눅스 커널의 특징 중 하나이며 유닉스에 비해 리눅스는 초창기부터 가상 파일 시스템을 지원했다.

2. 모든 파일 시스템을 하나의 파일 시스템으로 보이게 하는 계층(layer)이라 할 수 있다.

3. 파일, 디렉터리, 특수 파일 등을 파일 처리 시스템 호출(system call)을 통해 일관적으로 조작할 수 있다.

## 리눅스 디렉터리 구조
![image](blob:https://velog.io/b48fb361-0722-49bf-9da6-caa01ceced9a)

- 각각의 디렉터리는 그에 맞는 용도가 있다. 
| 디렉터리         | 설명                                                                                                                                                             |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /                | 시스템의 근간이 되는 디렉터리로, 모든 파티션 및 디렉터리는 여기에 위치하며 시스템의 중요한 부분입니다.                                                       |
| /bin             | 시스템 관리자나 일반 사용자가 실행하는 명령어들이 들어있는 디렉터리입니다.                                                                                      |
| /sbin            | 시스템 관리자가 사용하는 명령어들이 들어있으며 시스템 수정 및 복구와 관련된 명령어들이 있습니다. 일반 사용자의 실행 권한이 제한됩니다.                  |
| /boot            | 부트로더와 부팅과 관련된 파일들이 위치하는 디렉터리로, 시스템 부팅에 필요한 파일들이 들어있습니다. 손상될 경우 시스템 부팅이 어려울 수 있습니다.    |
| /home            | 각 사용자의 홈 디렉터리가 하위 디렉터리로 위치하며, 개인 사용자의 데이터와 설정 파일들이 보관됩니다.                                                     |
| /dev             | 시스템의 모든 장치가 파일로 표현되는 디렉터리입니다. udev 데몬이 여기의 장치 파일을 관리하며, 예를 들어 /dev/sda, /dev/tty1 등이 있습니다.                |
| /etc             | 시스템이나 프로그램의 환경 설정 파일들이 위치하며, 시스템 관리 작업에서 주로 수정되는 곳입니다. 설정 파일은 보통 백업을 유지하는 것이 좋습니다.           |
| /lib             | 시스템 프로그램 실행에 필요한 공유 라이브러리들이 위치하며, 변경이나 삭제를 피하는 것이 좋습니다.                                                      |
| /mnt             | 마운트를 위한 임시 디렉터리가 위치하며, 이동 디스크(CD, USB 등)를 마운트할 때 사용됩니다.                                                            |
| /root            | root 계정의 홈 디렉터리로, root만 접근할 수 있습니다.                                                                                                   |
| /var             | 로그 파일 등 시시각각 업데이트되는 파일들이 위치하며, 시스템 운영에 필요한 파일도 위치합니다. 수정 및 삭제 시 주의가 필요합니다.                        |

### free
시스템의 메모리 정보를 출력
