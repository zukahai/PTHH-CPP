## <p align="center"> Cân bằng Phương trình hóa học bằng C++ </p>
<p align="center"> <img src="https://github.com/zukahai/HaiZuka/blob/master/Images/PTHH/1.png" alt="Tieude" /> </p>

## Cân Bằng Phương Trình Hóa Học Bằng C++
Hóa học là một nỗi sợ và có thể nói là nỗi ám ảnh của đa số học sinh phải không nào, các phương trình thực sự quá phức tạp ở giai đoạn cân bằng phương trình, vậy nếu như chúng ta tạo ra một chương trình cho phép cân bằng PTHH một cách chớp nhoáng thì sao nhỉ?

### 1. Phương trình hóa học và cân bằng phương trình hóa học là gì?
Phương trình hóa học (hay Phương trình biểu diễn phản ứng hoá học ) là một phương trình gồm có hai vế nối với nhau bởi dấu mũi tên từ trái sang phải, vế trái biểu diễn các chất tham gia phản ứng, vế phải biểu diễn các chất thu được sau phản ứng, tất cả các chất đều được viết bằng công thức hoá học của chúng và có những hệ số phù hợp đặt trước công thức hoá học đó để bảo đảm đúng định luật bảo toàn khối lượng.
Việc tìm ra các hệ số đặt trước các chất trước và sau phản ứng đó được gọi là cân bằng phương trình hóa học.
Ví dụ về phương trình hóa học (đã được cân bằng):
2H2 + O2 → 2H2O
4Fe + 6HCl → 2Fe2Cl3 + 3H2
CaCO3 → CaO + CO2
### 2. Ý tưởng thuật toán
Với bài toán cân bằng phương trình hóa học ta cần làm như thế nào? Có rất nhiều cách cân bằng phương trình hóa học, một số đó là định luật bảo toàn khối lượng, có nghĩa là khối lượng các chất trước và sau khi phản ứng không đổi, điều này có nghĩa là số mol của mỗi nguyên tố hóa học tham gia phản ứng của được bảo toàn.

Ví dụ như phương trình sau:

2H2 + O2 → 2H2O

Trước và sau khi phản ứng đều có 4 đơn vị mol Hidro và 2 đơn vị mol Oxi

Bám sát vào điều này ta thấy rằng nếu đặt các hệ số trước các chất trước và sau khi phản ứng bằng các ẩn thì với mỗi nguyên tố học học ta sẽ thu được một phương trình.

Với PTHH:

Al + HCl  → AlCl3 + H2

Ta có thể đặt các ẩn số trước tất cả các chất trước và sau phản ứng và việc của chúng ta cần làm là tìm ra chúng

a Al + b HCl  → c AlCl3 + d H2

Lúc này ta áp dụng định luật bảo toàn nguyên tố ta có các phương trình sau:

- Với nguyên tố Al: a = c
- Với nguyên tố H: b = 2d
- Với nguyên tố Cl: b = 3c
Như thế ta đã có hệ phương trình 3 phương trình và 4 ẩn số, hệ này vô số nghiệm, việc ta cần làm là tìm ra bộ nghiệm tối giản của hệ phương trình trên (hệ số tối giản khi các hệ số đều là số nguyên dương và ước chúng lớn nhất của tất cả các số đó bằng 1)

Ý tưởng chính của bài này là sẽ đặt N biến là N hệ số trước N chất trước và sau phản ứng, từ M nguyên tố có trong phương trình ta đưa ra được M phương trình, từ đó ta có hệ phương trình (HPT) bậc nhất N ẩn, M phương trình, sau đó ta sẽ giải hệ phương trình đó bằng ma trận tuyến tính để tìm ra các hệ số của PTHH.

### 3. Giải hệ phương trình bằng ma trận tuyến tính
Ví dụ cho phương trình sau và yêu cầu cân bằng nó:
H2 + O2 = H2O (Mình sẽ dùng dấu '=' để thay cho ký tự '→')

Sau khi cân bằng PTHH hoàn chỉnh sẽ là:
2H2 + O2 = 2H2O

Vậy làm thế nào để cần bằng được như thế, có nhiều cách để cân bằng PTHH, một trong số cách đó là dùng đến ma trận tuyến tính (MTTT), tại sai PTHH lại liên quan đến MTTT.
Như đã nói, ý tưởng chính của bài này là sẽ đặt N biến là N hệ số trước N chất trước và sau phản ứng, từ M nguyên tố có trong phương trình ta đưa ra được M phương trình, từ đó ta có hệ phương trình (HPT) bậc nhất N ẩn, M phương trình:

Ví dụ như với phương trình H2 + O2 = H2O
Ta sẽ đặt biến x, y, z lần lượt là hệ số trước H2, O2, H2O
Lúc này phương trình sau khi cân bằng sẽ có dạng:
xH2 + yO2 = zH2O
Với nguyên tố H ta có phương trình: 2x - 2z = 0
Với nguyên tố O ta có phương trình: 2y - z = 0
Sẽ có một số phương trình vô nghĩa, ví dụ như hệ phương trình:
a + b - c = 0
a + 2b = 0
2a + 3b - c = 0
Ta thấy phương trình 3 là phương trình vô nghĩa vì nó có thể được tạo ra từ phương trình 1 và 2, ta cần loại tất cả những phương trình vô nghĩa.
Đầu tiên ta đưa HPT đó và MTTT, tiếp đó bằng cách áp dụng phương pháp tìm hạng của ma trận mà ta loại bỏ được những phương trình vô nghĩa, hạng phương trình đó chắc chắn sẽ là N - 1.
Cuối cùng ta sẽ có hệ phương trình N ẩn với N - 1 phương trình, áp dụng giải HPT bằng MTTT ta sẽ có được vô số nghiệm theo một biến t nào đó (t là một hệ số bất kỳ trong các hệ số, bước cuối là chọn giá trị của biến t sao cho các hệ số là các số nguyên dương và ước chung lớn nhất của chúng là 1.
Để làm được như vậy bạn cần biết cách biến ma trận đó về dạng ma trận đường chéo.
Sau đây là một số ví dụ cho các bạn dễ hiểu hơn về phần này:
+) Với phương trình:
a H2 + b O2 → c H2O
Ta sẽ có hệ phương trình:
Với nguyên tố H: 2a = 2c <=> a = c
Với nguyên tố O: 2b = c
Với bài này tất cả hệ số đều biễu diễn theo c rồi nên ta chỉ việc chọn c hợp lý nữa là được (mình sẽ nói vấn đề này sau), mình sẽ tìm đươc c = 2, sẽ tình ra được a = 2, b = 1.
PT sau khi cân bằng: 2H2 + O2 → 2H2O
+) Với phương trình:
a Al + b HCl  → c AlCl3 + d H2
Với nguyên tố Al: a = c
Với nguyên tố H: b = 2d
Với nguyên tố Cl: b = 3c
Ta có hệ phương trình:
a + 0b - c + 0d = 0
0a + b + 0c - 2d = 0
0a + b - 3c + 0d = 0
Ta sẽ đưa hệ trên vào ma trận tuyến tính và biến đổi nó về ma trận đường chéo:
<p align="center"> <img src="https://github.com/zukahai/HaiZuka/blob/master/Images/PTHH/2.png" alt="Imblog" /> </p>
Lúc này ta có hệ phương trình:
3a = 2d
b = 2d
3c = 2d
Lúc này tất cả các hệ số đã được biểu diễn theo d, bây giờ chọn d thế nào để các hệ số là tối giản:
Đầu tiên cần tối giản các hệ số của từng phương trình một, ví dụ nếu có phương trình 2a = 4b thì bạn cần tối giản thành a = 2b:
Sau khi đã tối giản thì hệ số d cần tìm chính là bội chung nhỏ nhất của các hệ số phía bên trái.
Với trường hợp này d = bcnn(3, 1, 3) = 3, như vậy d = 3, a = 2, b = 6, c = 2;

PT sau khi cân bằng:
2Al + 6HCl  → 2AlCl3 + 3H2

+) Với phương trình:
a Al + b H2SO4 → c Al2(SO4)3 + d H2
- Với nguyên tố Al: a = 2c
- Với nguyên tố S: b = 3c
- Với nguyên tố H: 2b = 2d
- Với nguyên tố O: 4b = 12c
Ta có hệ phương trình:
a + 0b - 2c + 0d = 0
0a + b - 3c + 0d = 0
0a + 2b + 0c - 2d = 0
0a + 4b - 12c + 0d = 0
Ta sẽ đưa hệ trên vào ma trận tuyến tính và biến đổi nó về ma trận đường chéo:
<p align="center"> <img src="https://github.com/zukahai/HaiZuka/blob/master/Images/PTHH/3.png" alt="Imblog" /> </p>
Lúc này ta có hệ:
- 3a = 2d
- 2b = 2d
- 6c = 2d

Hệ sau khi rút gọn
- 3a = 2d
- b = d
- 3c = d
d = bcnn(3, 1, 3) = 3, a = 2, b = 3, c = 1

2Al + 3H2SO4 → Al2(SO4)3 + 3H2

### 4. Kết
Trên đây là các mà mình đã viết ra chương trình cân bằng phương trình hóa học, các bạn có thể tham khảo code c++ của mình [Tại đây](https://github.com/zukahai/PTHH-CPP/blob/master/PTHH.cpp)

Video demo:
[<p align="center"> <img src="https://github.com/zukahai/HaiZuka/blob/master/Images/PTHH/4.png" alt="blogimage" /> </p>](https://codelearn.io/Media/Default/Users/HaiZuka/HaiZuka/HaiZuka.mp4)

## <p align="center">  :tv: Thanks for whatching :earth_africa: </p>
