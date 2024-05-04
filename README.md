# Multi line display text
An simple core shader allows you make multiple layer text component.

# How this core shader can help you?
There's some issues in minecraft font and text display component.

- Text's ascent value cannot be more than it's height.
- If two different images overlapped, z-fighting problem is occurred.

But, this core shader removes all of this problem!

# Comparison
![녹화_2024_05_03_10_03_28_717-min](https://github.com/toxicity188/mult-layer-display-text/assets/114675706/161e5af4-7e13-4373-9028-7ff634dc8788)  
Normal core shader, occurring z-fighting problem.
![녹화_2024_05_03_10_05_19_637-min (1)](https://github.com/toxicity188/mult-layer-display-text/assets/114675706/5f367ad1-d75b-432e-a56c-a9bc9bdb40a0)  
My shader. no z-fighting!

# How to use?
``` json
{"type":"bitmap","file":"betterhealthbar:default_layout/image/1/empty_empty.png","ascent":-8192,"height":4,"chars":["򰀀"]}
```
First, you should minuse **-8192** to your font ascent.

``` json
{"type":"bitmap","file":"betterhealthbar:splitter.png","ascent":-9999,"height":-2,"chars":["򠀀"]}
```
Then, merge your image by space font.

``` json
{"type":"space","advances":{"򮀀":-8192,"򮀁":-8191,"򮀂":-8190,"򮀃":-8189,"򮀄":-8188,"򮀅":-8187}}
```
Don't forget to use spliitter!

``` kotlin
        val display = TextDisplay(EntityType.TEXT_DISPLAY, (player.world as CraftWorld).handle).apply {
            billboardConstraints = Display.BillboardConstraints.CENTER //Must!!!!!!!
            entityData.run {
                set(Display.DATA_POS_ROT_INTERPOLATION_DURATION_ID, 1)
                set(TextDisplay.DATA_BACKGROUND_COLOR_ID, 0)
                set(TextDisplay.DATA_LINE_WIDTH_ID, Int.MAX_VALUE)
            }
            brightnessOverride = Brightness(15, 15)
            text = PaperAdventure.asVanilla(component)
        }
```
And, you can use display or amor stand. but don't forget to set the billboard of display to CENTER!

![mob_effect_absorption_absorption](https://github.com/toxicity188/mult-layer-display-text/assets/114675706/0ebe9dcb-9bf6-4451-8f28-729d046c512a)  
Now, you have to modify image's alpha value to 1~254 (the greater, the higher layer.)

# Result
![녹화_2024_05_05_01_48_15_383-min](https://github.com/toxicity188/mult-layer-display-text/assets/114675706/ae033d45-f040-486e-9943-6ce9c1cf6bc6)  
Enjoy your multi line text display!
