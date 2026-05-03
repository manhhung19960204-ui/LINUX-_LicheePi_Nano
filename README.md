EMBEDDED LINUX - LICHEEPI NANO

Sản phẩm cuối cùng : Download u-boot-sunxi-with-spl.bin  https://drive.google.com/drive/u/1/folders/1Q5pth0KcZJTVVK6plZnPpDrBxEI-p6PS

Mô tả: File đã được build thành công cho kiến trúc ARM (Lichee Pi Nano), bao gồm cả SPL và U-Boot.

Bộ mã nguồn đầy đủ (SDK): Download licheepi_nano_sdk.tar.gz https://drive.google.com/drive/u/1/folders/1Q5pth0KcZJTVVK6plZnPpDrBxEI-p6PS

Bước 1: Kích hoạt nền tảng ảo hóa trên Windows
 Trước khi cài được Linux, phải cho phép Windows chạy chế độ máy ảo.

 Thực hiện: Mở Command Prompt , chạy lệnh wsl --install.
 Kết quả: Hệ thống đã bật Virtual Machine Platform và Windows Subsystem for Linux.
 

Bước 2: Cài đặt hệ điều hành Ubuntu (WSL2)
 Sử dụng Docker để thiết lập môi trường Build

 *Tại sao dùng Docker? Thay vì cài đặt trực tiếp các công cụ build lên Ubuntu có thể gây lỗi xung đột thư viện, em sử dụng Docker để đảm bảo môi trường build  ổn định, sạch sẽ 
 
 Lưu ý: Khi gõ mật khẩu trong Linux, màn hình sẽ không hiện ký tự, cứ gõ xong rồi Enter.
![Mô tả ảnh](image/UbuntuInstall.png)
_ Cập nhật hệ thống để giúp Ubuntu luôn ở trạng thái mới nhât : sudo apt update && sudo apt upgrade -y
_ Cài đặt Dependencies cho hệ thống : sudo apt install -y build-essential libncurses5-dev libssl-dev bison flex \ git bc u-boot-tools device-tree-compiler gcc-arm-linux-gnueabi \ python3 python3-dev python3-setuptools swig libelf-dev wget

Bước 3 : tải mã nguồn buildroot và tạo thư mục 
 _ tạo thư mục : mkdir ~/licheepi_nano
 _ Tải build root : git clone https://github.com/buildroot/buildroot.git --depth=1
cd buildroot
 _ chạy thử : make menuconfig
 ![Mô tả ảnh](image/RunBuildRoot.png)
 _ Buildroot thành công 
 ![Mô tả ảnh](image/BuildRootComplete.png)
 _ Build U-Boot Lichee Pi Nano thành công
  Lệnh cấu hình: make ARCH=arm licheepi_nano_defconfig
  Lệnh build: make ARCH=arm CROSS_COMPILE=arm-linux-gnueabi- -j$(nproc)
  ![Mô tả ảnh](image/BuildUBoot.png)
_ Hoàn thành RootFS
  ![Mô tả ảnh](image/CompleteRootfs.png)







 