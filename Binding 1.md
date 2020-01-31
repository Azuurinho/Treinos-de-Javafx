 IntegerProperty x= new SimpleIntegerProperty(2);      
        IntegerProperty y= new SimpleIntegerProperty();

        y.bind(x.multiply(10));
        System.out.println(x.getValue());
        System.out.println(y.getValue());

        x.setValue(9);
        System.out.println(x.getValue());
        System.out.println(y.getValue());
