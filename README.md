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
        Menu editMenu = new Menu("_Editar");
        editMenu.getItems().add(new MenuItem("Cortar..."));
        editMenu.getItems().add(new MenuItem("Copiar..."));

        //Menu de Arquivo
        Menu arquivoMenu = new Menu("_Arquivo");
        MenuItem novoArquivo = new MenuItem("Novo...");
        novoArquivo.setOnAction(e -> System.out.println("Criar novo arquivo!"));   // comando necessário pra que um item do menu tenha uma funcionalidade básica
        arquivoMenu.getItems().add(novoArquivo);
        arquivoMenu.getItems().add(new MenuItem("Salvar..."));
        arquivoMenu.getItems().add(new MenuItem("Configurações..."));
        arquivoMenu.getItems().add(new SeparatorMenuItem());                    // essa linha cria separações entre itens do menu
        arquivoMenu.getItems().add(new MenuItem("Save..."));
        arquivoMenu.getItems().add(new SeparatorMenuItem());
        arquivoMenu.getItems().add(new MenuItem("Sair..."));

        MenuItem paste = new MenuItem("Colar...");
        paste.setOnAction(event -> System.out.println("pasting some crap"));
        paste.setDisable(true);                                                 // faz com que seja impossível interagir com o item do menu
        editMenu.getItems().add(paste);

        //Menu Tamanho das letras
        Menu tamaMenu = new Menu("Tamanho da Fonte");
        ToggleGroup tamaToggle = new ToggleGroup();                            // Togglegroups vão ter opções que podem ser selecionadas,
        RadioMenuItem pequena = new RadioMenuItem("Pequena");             // porém só uma poderá ser selecionada de cada vez.
        RadioMenuItem media = new RadioMenuItem("Média");                 // Quando uma for selecionada, a outra será desmarcada.
        RadioMenuItem grande = new RadioMenuItem("Grande");
        pequena.setToggleGroup(tamaToggle);
        media.setToggleGroup(tamaToggle);
        grande.setToggleGroup(tamaToggle);
        tamaMenu.getItems().addAll(pequena, media, grande);                     // elas (opções) devem ser adicionadas ao menu separadamente.

        //MenuBar
        MenuBar menuBar = new MenuBar();
        menuBar.getMenus().addAll(arquivoMenu, editMenu, helpMenu,tamaMenu);

        VBox layout = new VBox(20);
        layout.getChildren().addAll();
        window.setScene(new Scene(menuBar, 500, 500));
        window.show();
    }

}
