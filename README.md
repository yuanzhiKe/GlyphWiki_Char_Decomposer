# GlyphWiki_Char_Decomposer
Chinese character decomposer based on Glyphwiki dump
## Structure of a GlyphWiki dump  
*NOte: I am not the author of glyphwiki. Here is just my understanding.*  

    Name  |Related| Shape Information  
    u5475 |u5475  |99:0:0:4:-1:187:195:u53e3-01$99:0:0:-27:0:202:200:u53ef-02  
    
Here is an example, u5475 is the unicode of '呵' and the name of the corresponding page on Glyphwiki.  
When you open the glyph wiki dump, you may see a lot of aji-xxxxx, c-beta-xxxxx. They are the code in another encoding. Related indicates the unicode (I believe). And don't worry, the unicode versions are in the list too. They are just put behind.  

Then let us see the sequence of the numbers in the 3rd column.

    99:0:0:4:-1:187:195:u53e3-01$99:0:0:-27:0:202:200:u53ef-02
    
This example has two glyph components:

    99:0:0:4:-1:187:195:u53e3-01
    
and

    99:0:0:-27:0:202:200:u53ef-02
    
They are segmented by '$'.  
The unicode like sequence (e.g. 'u53e3-01') is the unicode of the radical. And the numbers before the code is to describe the shape of the font. If you can read Japanese and want to learn more, check the following:

    上地宏一,「KAGEシステム: グリフ配信と生成文字品質の向上にむけて」,CHISE Symposium 2003, 東京, 2003年3月15日.
    
## What does this project do?

These codes are used to decompose every Chinese characters into radicals in the file. i.e. Replace every Chinese character with the unicode of the radical with a segmentation symbol. e.g: 

    '呵' ----> $$u53e3-01$$u53ef-02

## Usage

    python main.py -i [input_file] -o [ouput_file]
    
GlyphWiki dump will be automatically downloaded, and parsed. A .pkl containing the mapping dictionary of the characters and radicals will be generated as well.
