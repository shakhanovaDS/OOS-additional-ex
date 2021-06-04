# OOS-additional-ex

# Клонируем репозиторий с гита с папку SOURCES
git clone https://github.com/parazyd/git-restrict

# Переименовываем репозиторий в git-resrict-1.0 
mv git-restrict git-restrict-1.0

# Архивируем его
tar cvfz git-restrict-1.0.tar.gz git-restrict-1.0

# В папке SPECS добавляем файл git-restrict.spec
nano git-restict.spec

# Выполняем сборку пакета
rpmbuild -ba git-rectrict.spec

# Проверяем, что все зависимости есть
rpm -qp git-restrict-1.0-1.fc34.src.rpm --requires

# Заходим в SOURCES/git-restrict-1.0 и вызываем test.sh. Там он должен написать, что все тесты пройдены
./test.sh

# Запускаем службу haveged
sudo systemctl enable haveged
sudo systemctl start haveged

# Генерируем ключ
gpg2 --gen-key

# Экспортируем ключ
gpg2 --export -a 'Shakhanova Daria' > ~/rpmbuild/RPM-GPG-KEY-Shakhanova-Daria

# Подписываем все пакеты
rpm --addsing ~/rpmbuild/RPMS/*/*.rmp
