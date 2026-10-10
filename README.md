# Infinite Drag for EffectCraft

Бесконечное перетаскивание числовых значений.

Курсор переносится через край монитора, а число продолжает меняться без скачка. Работает в числовых полях эффектов, трансформаций, текста и диалогов. Учитываются масштаб интерфейса, смещение монитора, отпускание кнопки и потеря фокуса. Одно удержание мыши — один шаг Undo.

Native monitor-edge cursor wrapping for continuous numeric editing in EffectCraft.

## Применение

Патч рассчитан на [EffectCraft](https://github.com/storytold/effectcraft) commit `608d1b077b65bb7591f26be587a2a5a47f4278bc`.
Он применяется отдельно от двух других функциональных патчей. Готовые исходники со всеми
изменениями и Windows-сборка: [effectcraft-custom](https://github.com/kikikikier/effectcraft-custom).

```powershell
git clone https://github.com/kikikikier/effectcraft-infinite-drag.git
git clone https://github.com/storytold/effectcraft.git
Set-Location effectcraft
git checkout 608d1b077b65bb7591f26be587a2a5a47f4278bc
git apply --check ../effectcraft-infinite-drag/effectcraft-infinite-drag.patch
git apply ../effectcraft-infinite-drag/effectcraft-infinite-drag.patch
# Общая правка оформления применяется один раз, даже если установлены несколько патчей.
git apply ../effectcraft-infinite-drag/custom-build-branding.patch
cargo +1.95.0 build --locked --release -p effectcraft
```

Патчи не предназначены для произвольной новой версии upstream без проверки совместимости.
Если распространяете свою изменённую сборку, удалите также файлы фирменных знаков из
`docs/brand/` и их изображения в документации согласно условиям upstream.

## Проверка

```powershell
cargo +1.95.0 test --release -p effectcraft-ui-egui --lib pointer_wrap::tests
```

Проверена применимость каждого патча к чистому базовому commit и совместимость всех трёх
патчей во всех шести порядках применения. Подробности проверки общей сборки — в
[отчёте](https://github.com/kikikikier/effectcraft-custom/blob/main/CUSTOM-BUILD.md).

## Связанные репозитории

- [effectcraft-type-in-font-search](https://github.com/kikikikier/effectcraft-type-in-font-search)
- [effectcraft-textbox-plugin](https://github.com/kikikikier/effectcraft-textbox-plugin)
- [Все изменения вместе](https://github.com/kikikikier/effectcraft-custom)

## Происхождение и лицензия

Основано на EffectCraft команды ArtCraft и участников проекта. Это независимые изменения,
а не официальный релиз upstream. Лицензия кода: **MIT OR Apache-2.0**; уведомления об авторстве
сохранены в [NOTICE](NOTICE), [LICENSE-MIT](LICENSE-MIT) и [LICENSE-APACHE](LICENSE-APACHE).
