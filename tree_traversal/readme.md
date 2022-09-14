### Muqaddimah

Pertama mari kita coba revisit materi `Binary Tree` yang ada di kuliahan, silahkan lihat [refrensi disini ](https://en.wikipedia.org/wiki/Binary_tree)
In-short `Binary Tree` adalah sebuah `Tree` dengan sebuah rules untuk memempatkan setiap `Node` nya.

### Traversal

Traversal adalah sebuah term atau sebuah proses untuk mencari sebuah `Node` yang ada di dalam `Tree`.
Oke, mungkin cara termudah untuk <s>melupakan mantan</s> melakukan `Traversal` adalah mengunjungi setiap node yang ada dan mencoba untuk 
<s>melupakannya</s>  mencocokannya. Tapi, bukannya `Tree` adalah `non-linear data structure` kita tidak bisa melakukan `looping by index` seperti di array
bukan?, lalu harus bagaimanakah aku bisa untuk <s>mendapatkan hatinya</s> meng-coding nya

### DFS Traversal

DFS Traversal adalah sebuah teknik `Traversal` dimana kita akan berkunjung dulu ke `Node` Terbawah yang di sebelah `kiri` sampai ujung `Node` Tersebut
lalu berkunjung ke `kanan`. Anda bingung? sama saya juga.., tapi coba kita simak ilustrasi di bawah ini

<br />

<img src="https://miro.medium.com/max/1280/0*miG6xdyYzdvrB67S.gif" alt="MarineGEO circle logo" style="height: 200px; width:400px;"/>

### Pre-implementation

Oke, kita sudah melihat cara kerja dari `DFS Traversal` but, bagaimanakah cara <s>mendapatkannya</s>  meng-implementasikannya, So, mari rencakan
code yang akan kita buat :

- Buat sebuah `function` untuk melakukan visit terhadap setiap node
- Lalu pertama yang akan kita lakukan adalah, check apakah tree tersebut kosong [kayak hati aku tanpa kamu :D]
- lalu setelah itu kita check apakah `left node` nya ada, jika ada maka kita akan panggil lagi function tersebut (baca: recursive) untuk
mengunjungi `let node` dari `left node` tersebut
- lakukan hal yang sama untuk `right node`

### Nguli Moment

daripada lihat disini, lebih enak kalau anda melihat code nya di file `.ipynb` yang sudah saya sediakan.

`Node Class For Constructing A Tree`

```python
class Node:
    
    def __init__(self, data = None):
        self.left = None
        self.data = data
        self.right = None
        
    def insert(self, data):
        if self.data:
            if data < self.data:
                if self.left is None:
                    self.left = Node(data)
                else:
                    self.left.insert(data)
            elif data > self.data:
                if self.right is None:
                    self.right = Node(data)
                else:
                    self.right.insert(data)
            else:
                return
        else:
            self.data = data
```

`Seeding Tree`

```python
node = Node(10)
node.insert(11)
node.insert(9)
node.insert(8)
node.insert(12)
```

`DFS Traversal Tree`

```python
def dfsPrint(tree):
    if tree is None:
        return
    else:
        if tree.left:
            print('To left')
            dfsPrint(tree.left)
        print(tree.data)
        if tree.right:
            print('To right')
            dfsPrint(tree.right)
```

`Call Me Baby`

```python
dfsPrint(node)
```

### Real world implementation

`DFS Traversal` theorem di-implementasikan di `Assembly Syntax Tree` aka `AST`, terdengar asing? kalau anda familiar
mungkin anda sudah bisa membuat bahasa pemograman sendiri.., serius nggk bohong.., mari kita lihat aja contoh di bawah ini :

<br />

<img src="https://ruslanspivak.com/lsbasi-part7/lsbasi_part7_astimpl_01.png" alt="MarineGEO circle logo" style="height: 250px; width:400px;"/>

Jadi, misalnya kita mempunyai sebuah string `2 * 7 + 3`, lalu kita ingin membuat fungsi untuk melakukan operasi aritmatika berdasarkan isi string
tersebut. Mudah saja bagi kita (human) untuk melakukan operasi aritmatika di atas, pertama kita akan melakukan perkalian `2 * 7`, lalu hasil perkalian tersebut akan kita jumlahkan dengan `3`. Tapi bagaimana <s>caraku mendapatkannya</s> komputer melakukannya.

Yak, betul, sesuai ilustrasi di atas, kita dapat membuat sebuah `Tree` dimana, operasi yang akan kita lakukan akan kita taruh di `Node` terbawah.
Lalu kita bisa melakukan `Traverse` ke setiap `Node` dan melakukan operasi aritmatika yang ada..


### Disclaimer

Jangan di baca aja, ini bukan chat ku ke doi... :D, boleh banget berkontribusi untuk repo ini, caranya dengan fork, dan open pull request.
Repo ini bersifat terbuka (sama kayak hati aku, cuman nggk ada yang ngisi aja). Regards, 4RSIM3R - Galau Brutal