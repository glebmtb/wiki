```shell
touch .git/hooks/pre-commit  
chmod +x .git/hooks/pre-commit  

cat << 'EOF' > .git/hooks/pre-commit
#!/bin/bash

# Запускаем команду `./gradlew goJF` и сохраняем её вывод
OUTPUT=$(./gradlew goJF)

# Проверяем, есть ли строка "formatted successfully" в выводе
if echo "$OUTPUT" | grep -q "formatted successfully"; then
    echo "Ошибка: Есть несоответствующий формат, запустите ./gradlew goJF перед коммитом."
    exit 1
fi

# Если всё в порядке, позволяем продолжить коммит
exit 0
EOF
```

```shell
#!/bin/bash

# Запускаем команду `./gradlew goJF` и сохраняем её вывод
OUTPUT=$(./gradlew goJF)

# Проверяем, есть ли строка "formatted successfully" в выводе
if echo "$OUTPUT" | grep -q "formatted successfully"; then
    echo "Ошибка: Есть несоответствующий формат, запустите ./gradlew goJF перед коммитом."
    exit 1
fi

# Если всё в порядке, позволяем продолжить коммит
exit 0
```
