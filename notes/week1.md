��һ�ܱʼ�

�����Ѿ�֮ǰ��װ����IDEA�����ԱʼǷ�Ϊ�����֣�
1.���е�һ�ڿζ�Ӧ��ʾ������
2.ѧϰJAVA8�����ԣ�������Ϊ�򵥵ļ�������
3.����github�ֿ�ͱ��زֿ�

һ��Java-basics-codes
1.DataTypeDemo
	(1)ֱ�Ӷ��������
		float myFloatNum = 5.99f;
	(2)ÿ���������Ͷ��ж�Ӧ�ķ�װ�ࣺ
		Float myFloatNum2= 5.99f;
	(3)����ת����
		�Զ�ת����int myInt = 5;	double myDouble = myInt;
		ǿ��ת����double myDouble = 12.2d;		int myInt = (int) myDouble;
	(4)�ַ�����
		String greeting = "Hello world";
		�ַ������ӣ�System.out.println("myInt="+ myInt);
		
2.ArrayDemo
	(1)�������飺
		String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
	(2)���鳤�ȣ�
		System.out.println(cars.length);
	(3)for-eachѭ��
		for (String car : cars) {
            System.out.println(car);
        }
	(4)��ά���飺
		int[][] myNumbers = { {1, 2, 3, 4}, {5, 6,7} };
		
3.ooDemo
	(1)�����ࣺ��ȡ����Ĺ�ͬ����
		public abstract class Animal {
			String name;

			public Animal() {
				name = "Animal";
			}
			public abstract void eat();		//����һ��Ҫʵ�ָ���ĳ��󷽷�

			public void sleep(){			//���������д�����еķǳ��󷽷�
				System.out.println(name+"����˯");
			}
		}
	(2)�ӿ��ࣺ������ʾ������Ϊ��javaû�ж�̳У�����ͨ���ӿ�ʵ�֡�
		public interface Flyable {
			void fly();
		}
	(3)��̬�����뿴��ߣ�ʵ�ֿ��ұ�
		Animal[] animals = new Animal[]{
             new Animal(),new Bird(),new Mouse()
        };
        for(Animal animal:animals){
            animal.eat(); //���ݲ�ͬ�Ķ������ͣ����ò�ͬ��eat����
        }
	(4)���ڽӿڵĶ�̬��
		Flyable[] flyables = new Flyable[]{
                new Bird(),new AirPlane()	//����ʵ��Flyable�ӿڣ�ʵ��fly����
        };
        for(Flyable flyable:flyables){
            flyable.fly(); //���ݲ�ͬ�Ķ������ͣ����ò�ͬ��fly����
        }
	(5)�ӿ���Ϊ������
		public static void startToFly(Flyable flyable){
			flyable.fly();
		}
		for(Flyable flyable:flyables){
            startToFly(flyable); //���÷���������ӿ����ͱ���
        }

4.ListDemo
	(1)���壺
		ArrayList<String> list=new ArrayList<>();
	(2)���룺
		list.add("World");
        list.add(0,"HAHAHAHA");
	(3)ȡֵ����ң�
		System.out.println(list.size());
        System.out.println(list.get(0));
        //�ж��Ƿ����ĳ��Ԫ��,�����Ԫ�ص���Equals�����Աȣ�����Boolean
        System.out.println(list.contains("World"));
	(4)������
		//���±�
		for(int i=0;i<list.size();i++){
            System.out.println(list.get(i));
        }
		//for-eachѭ��
		for (String str : list) {
            System.out.println(str);
        }
		
		//ʹ��stream��lambda���ʽ���б���
        list.stream().forEach(item-> System.out.println(item));
	(5)����
		//ʹ��lambda��Ϊ�Ƚ���������
		Collections.sort(list,(i1,i2)-> i2.compareTo(i1));
		
5.MapDemo
	(1)���壺
		Map<String, String> map = new HashMap<String, String>();
	(2)���룺
		map.put("1", "google");
	(3)������
		//���ã�����ȡֵ���Ȼ�ȡkeyֵ���ٻ�ȡkey��Ӧֵ
		for (String key : map.keySet()) {
            System.out.println("key= "+ key + " and value= " + map.get(key));
        }
		
		//������ʱ�����Ƽ�����entry��ȡÿһ������ֵ��
        for (Map.Entry<String, String> entry : map.entrySet()) {
            System.out.println("key= " + entry.getKey() + " and value= " + entry.getValue());
        }
		
����Java8������֮��
1.Lambda ���ʽ��Lambda ����Ѻ�����Ϊһ�������Ĳ�����������Ϊ�������ݵ������У���
	//���������eΪ�����������ɱ���������õ�
	Arrays.asList( "a", "b", "d" ).forEach( e -> System.out.println( e ) );
	//����list��Ϊ���������շ���ֵ������ֵ�����ɱ���������õ�
	Collections.sort(list,(i1,i2)-> i2.compareTo(i1));
	
2.�������ã���������ʹ�ÿ����߿���ֱ�������ִ�ķ�����Java��Ĺ��췽������ʵ������
	//ʾ����
	public static class Car {
		public static Car create( final Supplier< Car > supplier ) {
			return supplier.get();
		}              

		public static void collide( final Car car ) {
			System.out.println( "Collided " + car.toString() );
		}

		public void follow( final Car another ) {
			System.out.println( "Following the " + another.toString() );
		}
		
		public void repair() {   
			System.out.println( "Repaired " + this.toString() );
		}
	}
	(1)���캯�����ã�
		List< Car > cars = Arrays.asList( Car :: new );
	(2)��̬�������ã�
		cars.forEach( Car::collide );
	(3)��Ա�������ã�
		//�����ղ���
		cars.forEach( Car::repair );
	(4)ʵ������ķ������ã�
		final Car car = Car.create( Car::new );
		//����һ��Car���͵Ĳ���
		cars.forEach( car::follow );
		
��������github�ֿ�ͱ��زֿ�
1.��github�ϴ���һ�������ֿ�
2.�ڱ����½��ļ��У�����git bash:
	git init
	git add .
	git commit -m "��һ���ύ"
	git branch -M main
	git remote add orgin https://github.com/hhtdgit/JAVAEE.git
	git push -u origin main