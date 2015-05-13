## Writing Games with Ruby-Ruby On Ales 2014 ##

[Confreaks-Writing Games with Ruby](http://confreaks.tv/videos/roa2014-writing-games-with-ruby)

###簡介
寫遊戲程式和Ruby語言都是非常有趣的，我們何不利用Ruby語言來寫game呢?

在這個Confreak中可以學到遊戲中的基本概念以及利用Gosu library來實現，包括：game loop, sprites, animation, camera movement and hit detection。

###內容介紹
一開始，講者介紹了幾個使用Ruby寫成的遊戲，如:似馬力歐、跳火圈、按鍵出聲還有忍者避開蛇。

![](https://angelawang0712.files.wordpress.com/2015/05/game.png)

接著，說明game loop，是由一個循環組成的，可由以下圖得知。

![game loop](https://angelawang0712.files.wordpress.com/2015/05/slide_21.jpg)

遊戲中也會有圖片或是音樂的資源來使用。

**我們開始正題吧！**

- **Gosu::Window**

首先，進到[https://www.libgosu.org/rdoc/](https://www.libgosu.org/rdoc/)網頁，在右邊Class List中，找到Window Class，初始化視窗**(程式的部分，講者有放在github中)**

    (Window) initialize(width, height, fullscreen, update_interval = 16.666666)

就會產生出一的視窗畫面出來了，增加一個方法可以利用向下鍵來使視窗關閉

    def button_down id
      close if id == Gosu::KbEscape
    end
顯示圖像在視窗中

    @image = Gosu::Image.from_text self,
                                  "Hello world!",
                                   Gosu.default_font_name,
                                   100

並新增一個draw的方法

    def draw
      @image.draw @image_x, @image_y, 1
    end
這樣就會有一個顯示Hello world!的視窗出來了，在上面使用到的是<code>Gosu::Window</code>、<code>Gosu::Image</code>、<code>from_text</code>語法

- **Screen Coordinates**

![Screen Coordinates](https://angelawang0712.files.wordpress.com/2015/05/slide_28.jpg)

這是常會用到的觀念，視窗的位置，如果想要上面的範例文字置中的話，就需要這樣改

    def update
      @image_x  = self.width/2 - @image.width/2
      @image_y  = self.height/2 - @image.height/2
    end
並且加上這兩行，就可以使文字動起來~~

      @image_x += 150 * Math.sin(Time.now.to_f)
      @image_y += 100 * Math.tan(Time.now.to_f)

- **Gosu::Song**

加入音樂，調整音量

    @music = Gosu::Song.new "XXX.mp3"
    @music.valume = 0.15
    @music.play
利用按鍵來發出聲音

    @beep = Gosu::Sample.new "beep.wav"
    @beep.play if id == Gosu::KbEscape

- **Sprite**

製作小精靈，可以讓它看起來是會動的**(程式的部分，講者有放在github中)**

![](https://angelawang0712.files.wordpress.com/2015/05/slide_38.jpg)

###講者
![Mike Moore](https://avatars2.githubusercontent.com/u/730?v=3&s=400)

**Mike Moore**

[twitter](https://twitter.com/blowmage)


###Slide 與 Github 連結

[Writing Games with Ruby-Slide](http://conferences-box.com/conferences/45/sessions/1197/slideshow)

[writing games rbonales 2014-Github](https://github.com/blowmage/writing_games_rbonales_2014)


###相關技術介紹

[https://www.libgosu.org/rdoc/](https://www.libgosu.org/rdoc/)

Gosu是2D遊戲開發的library，提供給Ruby和C++使用，並且可以在Mac、Windows和Linux中執行

Gosu只提供基本的模組

- 有loop和callback的視窗
- 2D圖形和文字
- 聲音樣本和音樂的各種格式
- 鍵盤、滑鼠和遊戲桿的輸入

###心得
透過Confreaks看到許多不同的議題，並選擇了看起來比較有趣的來做這次的期中研討會作業，也學到了原來Ruby也可以向其他語言一樣，也會有視窗畫面的呈現，可以做成遊戲，真的很有趣，也比其他語言簡潔多了，雖然這位講者並沒有全部講完，只講了一小部分，有可能是因為時間不夠的關係，覺得很厲害啊~~

像小精靈的範例，特別有感觸，因為之前有使用JavaScript寫過，結果講者並沒有特別完整的介紹，有點小小的失望，不然其實還蠻想了解使用Ruby寫法的小精靈，一定跟Javascript的寫法很不一樣。還有比較可惜的是沒有介紹到 camera movement 和 hit detection。很想知道是什麼的說。

總結來說，其他語言可以做到，Ruby一樣也可以~~實在是不會讓別的語言佔到便宜呢(笑)