# my README

original : https://github.com/qqwweee/keras-yolo3  
reference : https://tech-diary.net/keras-yolov3/

## 実行環境
python 3.6  
tensorflow 1.14.0(gpu版だと動作しなかった)  
keras 2.2.4  
pillow   
matplotlib  

## 実行方法
1. 物体検出を行う画像を/imageに入れる.
2. 下のコマンドを実行する.
```
python yolo_video.py --image
```
3. 実行してしばらくすると次のように表示されるから, 1.の画像のパスを入れる.
```
Input image filename:shibuya.jpg
```

4. オリジナルではTEMPフォルダに実行結果が保存されるが, yolo_video.pyを一部変更して/imageに画像が保存されるようにした. 変更部分は次の通り
```python
def detect_img(yolo):
    while True:
        img = input('Input image filename:')
        try:
            image = Image.open(img)
        except:
            print('Open Error! Try again!')
            continue
        else:
            r_image = yolo.detect_image(image)
            r_image.show()
            r_image.save("./image/detected_image.png") # 追加部分
    yolo.close_session()
```

