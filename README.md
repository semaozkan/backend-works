# JVM nedir ne işe yarar?
JVM java dilinin en önemli özelliği olan bir kere yaz her yerde çalıştır mantığını sağlayan mekanizmadır ve hemen her platforma uygun sürümü vardır. <br/>
Java kodları .java uzantılı dosyalara yazılır. Daha sonra bu dosya derlenerek byte koda dönüştürülür. Bu byte kodlar .class uzantılı dosyalara yazılır. Daha sonra bu byte kodlar JVM üzerinde çalıştırılır ve sistemin anlayacağı şekle dönüştürülür. Bu sayede java kodlarının her sistemde çalışabilmesi sağlanır. Örneğin Linux ve Windows birbirinden çok farklı platformlar olmasına rağmen Java ile geliştirilmiş bir yazılım bu iki platformda da bulunan Java Sanal Makinası sayesinde kullanılabiliyor.

# JDK nedir, ne işe yarar?
JDK, java uygulamaları geliştirmek için kullanılan bir yazılım geliştirme ortamıdır. İçerisinde JVM, JRE, java kütüphaneleri, Java Compiler ve Interpreter içerir. Bir java uygulaması geliştirmek için JDK yüklememiz yeterlidir. Çünkü JDK diğer araçları içirisinde barındırır.<br/><br/>
![jdk](https://i.pinimg.com/564x/51/8c/af/518caf43195be21da948835f6727cd1e.jpg)

# Garbage Collector görevi nedir? Nasıl çalışır?
Garbage Collector, otomatik bellek yönetimi mekanizmasıdır. Bu işlemde heap belleğine bakılır. Kullanılan objeler tespit edilir ve referans edilmeyenler/kullanılmayanlar silinir. Kullanılmayan nesnelerin kapladığı alan bellekte boşa çıkarılır ve boşuna yer kaplamamış olur. Bu işlemi yapan mekanizmaya da garbage collector denir.

# .jar formatı nedir?
.jar uzantılı JAR(Java Archive) dosyası JRE tarafından java dosyalarını ve bunlara bağlı meta verileri saklayan bir paket dosya formatıdır. Yani arşiv dosyasıdır. JAR dosyası ZIP formatındadır ve içinde javaya özgü bildirim dosyaları taşır.<br/>
JAR dosyası her şeyin toplu bir şekilde saklanmasını sağlar. Sıkıştırıldıkları için indirme süresini kısaltırlar.

# Javada .class ve .java formatının farkı nedir?
.java java programlama dilinde yazılmış bir java kaynak kodu dosyasıdır. .class'da ise java kaynak kodu dosyasının derlenmesi ile oluşan ve JVM tarafından okunabilen byte kodlar bulunur. Ayrıca yazılan kodu her yerde çalıştırabilmek için .java formatındaki dosyayı .class formatı dosyasına dönüştürmek gerekir. Çünkü .class formatındaki dosyalar JVM üzerinden programdan bağımsız çalışabilirken .java formatındaki dosyalar için bu mümkün değidir.

# Abstract class nedir, nasıl çalışır, ne işe yarar?
Ortak özellikleri olan nesneleri modellemek için abstract class kullanılır. Abstract classlar kalıtım özelliğini kullanarak kod tekrarını azaltırlar. Abstract classlardan nesne tanımlanamaz. Abstract classı extend eden class, abstract classın tüm abstract metodlarını override etmek zorundadır.

# Abstract class örenği
```
public class Abstractclasses {

    public static void main(String[] args) {

        AbstractDatabase abstractDatabase1 = new MySqlDatabase();
        AbstractDatabase abstractDatabase2 = new MongoDatabase();

        abstractDatabase1.add(); //Eklendi.
        abstractDatabase2.add(); //Eklendi.

        abstractDatabase1.update(); //MySql guncellendi.
        abstractDatabase2.update(); //MongoDb guncellendi.

        abstractDatabase1.delete(); //Silindi.
        abstractDatabase2.delete(); //Silindi.

        abstractDatabase1.get(); //MySql verileri aldi.
        abstractDatabase2.get(); //MongoDb verileri aldi.
    }
}


//Abstract class
public abstract class AbstractDatabase {
    
    public void add(){
        System.out.println("Eklendi.");
    }
    
    public void delete(){
        System.out.println("Silindi.");
    }
    
    abstract void update();
    abstract void get();  
}


public class MongoDatabase extends AbstractDatabase{

    @Override
    void update() {
        System.out.println("MongoDb guncelledi");
    }

    @Override
    void get() {
        System.out.println("MongoDb verileri aldi.");
    }   
}


public class MySqlDatabase extends AbstractDatabase{
    
    
    @Override
    void update() {
        System.out.println("MySql guncelledi");
        
    }

    @Override
    void get() {
        System.out.println("MySql verileri aldi.");
    }    
} 
```

