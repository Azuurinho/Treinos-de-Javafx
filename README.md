public class Main extends Application {
    
    Stage window;
    
    
    public static void main(String[] args) {
        launch(args);
    }
    
    @Override
    public void start(Stage primaryStage) {
        window = primaryStage;
        window.setTitle("CheckBox Exemple");
        Button btn = new Button("Enviar");
        
        //Menu File (Arquivo)
        Menu arquivoMenu = new Menu ("Arquivo");
        
        //Menu Items
        arquivoMenu.getItems().add(new MenuItem("Novo Projeto..."));
        arquivoMenu.getItems().add(new MenuItem("Novo Módulo..."));
        arquivoMenu.getItems().add(new MenuItem("Abrir Projeto..."));
        
        //Menu Bar
        MenuBar menuBar = new MenuBar ();
        menuBar.getMenus().add(arquivoMenu);
        
        VBox layout = new VBox (10);
        layout.setPadding(new Insets (20, 20, 20, 20));
        layout.getChildren().add(menuBar);
        Scene scene = new Scene (layout, 300, 300);
        window.setScene(scene);
        window.show();
    }
    
    
    
}
