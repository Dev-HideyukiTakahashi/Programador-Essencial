# :gem:JAVAFX
---

* A Oracle disponibiliza o código fonte do Scene Builder. Os builds para instalação são mantidos pela Gluon.
  * Scene Builder: https://gluonhq.com/products/scene-builder/
  * Window -> Preferences -> JavaFX
* Configurações antes de inciar:
  * JavaFX SDK: https://gluonhq.com/products/javafx/
  * Plug-in E(fx) no Eclipse
    * Help -> Install new Software > https://download.eclipse.org/efxclipse/updates-released/ (para ver a última versão) -> é só clicar e copiar o link
  * No arquivo main > Run As > Run Configuration > Arguments > VM Argumentos:
    * --module-path C:\java-libs\javafx-sdk-11\lib --add-modules=javafx.fxml,javafx.controls