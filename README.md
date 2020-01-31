public class Main extends Application {

    Stage window;

    public static void main(String[] args) {
        launch(args);
    }

    @Override
    public void start(Stage primaryStage) throws Exception{
        window = primaryStage;
        window.setTitle("Hello World");

        //Help Menu
        Menu helpMenu =new Menu("Ajuda");
        CheckMenuItem autoSave= new CheckMenuItem("Salvar Automaticamente");
        autoSave.setOnAction(event -> {                                             // Essa expressão verifica se um item do menu
            if (autoSave.isSelected()){                                             // está ou não selecionado, e tem dá a oportunidade
                System.out.println("O programa será salvo automaticamente.");       // de relizar métodos dependendo da situação;
            } else {                                                                //
                System.out.println("O programa não salvará automaticamente");       //
            }
        });
        autoSave.setSelected(true);                                                 // Isso faz com que por Default, o autosave esteja selecionado
        helpMenu.getItems().addAll(autoSave);

        //Edit Menu
        Menu editMenu = new Menu("_Edit");
        editMenu.getItems().add(new MenuItem("Cortar..."));
        editMenu.getItems().add(new MenuItem("Copiar..."));

        //File Menu
        Menu fileMenu = new Menu("_File");
        MenuItem newFile = new MenuItem("Novo...");
        newFile.setOnAction(e -> System.out.println("Criar novo arquivo!"));   // comando necessário pra que um item do menu tenha uma funcionalidade básica
        fileMenu.getItems().add(newFile);
        fileMenu.getItems().add(new MenuItem("Salvar..."));
        fileMenu.getItems().add(new MenuItem("Configurações..."));
        fileMenu.getItems().add(new SeparatorMenuItem());
        fileMenu.getItems().add(new MenuItem("Save..."));
        fileMenu.getItems().add(new SeparatorMenuItem());
        fileMenu.getItems().add(new MenuItem("Sair..."));

        MenuItem paste = new MenuItem("Colar...");
        paste.setOnAction(event -> System.out.println("pasting some crap"));
        paste.setDisable(true);                                                 //faz com que seja impossível interagir com o item do menu
        editMenu.getItems().add(paste);

        //MenuBar
        MenuBar menuBar = new MenuBar();
        menuBar.getMenus().addAll(fileMenu, editMenu, helpMenu);

        VBox layout = new VBox(20);
        layout.getChildren().addAll();
        window.setScene(new Scene(menuBar, 500, 500));
        window.show();
    }

}
