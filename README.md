# 1.hafta-backend-homework

•	JVM nedir ne işe yarar?
Derlenmiş java kodları .class dosyasında bytecode olarak saklanır. Bytecode makine dilidir ve platform bağımsızdır, JVM için üretilir. Her farklı makine bytecode ürettiği için derlayicinin işi kolaylaşır. Temel görevi class dosyalarını yorumlamaktır. Bytecode olarak sakladığı için Java'nın platform bağımsız çalışmasını sağlar.
 
•	JDK nedir ne işe yarar?
Java tabanlı uygulamaları geliştirmek için kullanılan yazılım paketi denebilir. JRE(Jva uygulamalarını çalıştırmak için gerekir.), API sınıfları seti, Java derleyici gibi Java uygulamaları ve küçük uygulamalarını yazmak için gereken ek dosyaları içerir. 

•	Garbage Collector görevi nedir? Nasıl çalışır?
Otomatik bellek yönetimi mekanizmasıdır. Kullanılan objeleri tespit eder ve referans edilmeyenleri siler. Kulanılmayan nesnelerin bellekte boşa çıkmasıyla boş alan elde edilir. Kısaca; "new" anahtar kelimesiyle nesne oluşturulur, uygulama heap belleğe gider eğer yer yoksa GC devreye gider ve gerekli alan tahsis edilir.

•	.jar formatı nedir?
Java ile yazılmış, .jar uzantılı arşiv dosyalarıdır; her şeyin derli toplu biçimde saklanmasını sağlar. JRE tarafından java dosyalarını ve bunlara bağlı meta verilerini saklayan bir paket dosya formatıdır. İçinde birden çok dosya olduğu için ZIP formatında olan JAR dosyası, içinde Java'ya özgü bildirim dosyaları taşır. Bildirim dosyaları, bu dosyanın hangi amaçla kullanılacağını açıklar.
 
•	Javada .class .ve .java formatının farkı nedir? 
.class dosyalarında bytecode'a çevrilmiş hali bulunur. .jar dosyaları java dilinde olan arşiv dosyalarıdır.

•	Abstract class nedir,nasıl çalışır,ne işe yarar, 1 tane abstract class örneği
Abstract (soylu) sınıflar, nesnesi yaratılamayan sınıflara denir. Ortak özellikleri olan nesneleri modellerken kullanılır. Override edilmesi gereken ve gerekmeyen methodlar yazılabilir.
Abstractlardan direkt nesne oluşturamayız ama alt sınıflara direkt referans olabiliyor. Kod tekrarını azaltır.
Somut; abstract olduğunu belirtmeden yazılır, extends eden her classta olmak zorunda değildir.
Soyut; abstract olduğu belirtilir ve extends eden her class bu methodu override etmek zorundadır. 

Örnek; 

public abstract class Cisim {
    
    private int yuzey_sayisi;

    public Cisim(int yuzey_sayisi) {
        this.yuzey_sayisi = yuzey_sayisi;
    }
    
    public void yuzeySayisi(){ //somut method
        System.out.println("Cismin Yüzey Sayısı: "+ yuzey_sayisi);
    }
    
    abstract void hacimHesapla();

    public int getYuzey_sayisi() {
        return yuzey_sayisi;
    }

    public void setYuzey_sayisi(int yuzey_sayisi) {
        this.yuzey_sayisi = yuzey_sayisi;
    }
    
}



public class Kup extends Cisim{
    
    private int kenar;

    public Kup(int yuzey_sayisi, int kenar) {
        super(yuzey_sayisi);
        this.kenar = kenar;
    }

    @Override
    void hacimHesapla() {
        System.out.println("Küpün hacmi: " + (kenar * kenar * kenar));
    }
    
}



public class Kure extends Cisim {
    
    private int yaricap;

    public Kure(int yuzey_sayisi, int yaricap) {
        super(yuzey_sayisi);
        this.yaricap = yaricap;
    }

    @Override
    void hacimHesapla() {
        int V = (int) (4 * Math.PI * yaricap * yaricap * yaricap);
        System.out.println("Kürenin Hacmi: " +  (double)(V/3));
    }
    
}


public class Main {
    
    public static void main(String[] args){
        Kure kure = new Kure(1, 2);
        System.out.println(kure.getYuzey_sayisi());//somut method
        kure.hacimHesapla();//soyut method
        
        Kup kup = new Kup(6, 5);
        System.out.println(kup.getYuzey_sayisi());
        kup.hacimHesapla();
        
    }
    
}
