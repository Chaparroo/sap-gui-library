<- [Previus](welcome_doc.md)
# Transaction


1. [Parameters](#parameters)
2. [Methods](#methods-transaction)

```python
Transaction(
    session:GuiSession Object,
    code:str="",
)
```

## Parameters: 
- session: GuiSession Object - Session with which the transaction will be initiated.
- code: str - Name assigned to the transaction.

## Examples

Remember to do the following before interacting with transactions 
```python
sap_instance=SapGui(
    conection = "YOUR CONECTION",
    user = "User",
    password = "Password",
)
session = sap_instance.get_session() #GuiSession Object
```


- ### Basic usage 1
    ```python
    MB52 = Transaction(session=session, code="MB52")
    MB52.start_transaction()
    MB52.select_variant(
        author=author,
        variant_name=variant_mb52
    )
    MB52.run_transaction()
    MB52.export_in_toolbar(45)
    MB52.select_export_and_download(
        address=address,
        name=file_mb52
    )
    MB52.end_transaction()
    ```

- ### Basic usage 1
    ```python
    COOISPI=Transaction(
        session=session,
        code="COOISPI"
    )
    COOISPI.start_transaction()
    COOISPI.select_variant(
        variant_author=author
        variant_name=variant_cooispi
    )
    COOISPI.run_transaction()
    COLUMNS_NAMES=COOISPI.get_column_names() #Change
    COOISPI.export_in_shell_or_grid()
    COOISPI.select_export_and_download(
        address=address,
        name=file_cooispi
    )
    COOISPI.end_transaction()
    ```


## Methods Transaction(...)

- start_transaction(self): open transaction

- end_transaction(self): end transaction

- get_code_transaction(self): return code of transaction

- lock_session_ui(self):  blocks user actions such as click and keystroke

- unlock_session_ui(self): unlocks user actions such as click and keystrokes

- select_variant(
    self,
    variant_author: str = "",
    variant_name: str = "",
    variant_type: Literal["Click", "Author"] = "Author")  select the variant corresponding to the user or name 

- run_transaction(self, 
    bttn: Literal["Execute", "Continue"] = "Execute"): execute transaction

- get_shell_id(self,dictionary:dict={}) -> str: inside of execute transaction searh the first shell or grid id.
param dictionary optional

- get_column_names(self, grid_id:str=None) -> list[str]: get the columns names of the table

- export_in_shell_or_grid(
    self,
    btn_id_expand: str = "&NAVIGATION_PROFILE_TOOLBAR_EXPAND",
    btn_id_export: str = "&MB_EXPORT",
    item_menu: str = "&PC"):
    Searches for the export button within the toolbar contained in the grid.

- export_in_toolbar(self, number_button: str):Presses the export button on the toolbar.

- export_in_menu(self, step_to_export: list[int] = [0, 1, 2]):Option to export from the menu bar.

- select_export_and_download(self,
    address: str,
    name: str,
    type_export: Literal["0", "1", "2"] = "1",
    encoding: str = "4310",
    selection: Literal["Create", "Replace", "Add"] = "Replace"
):Controls the export window.

- select_value_in_shell(
    self, 
    shell_id: str, 
    name_label: str = "", 
    value_to_search: str = ""
): Allows selecting a value from gridView type tables.

- select_value_in_tables_type_label(
    self,
    container_id: str,
    column: int,
    value: str,
    virtual_key_page: int = 82,
    virtual_key_enter: int = 0
):Allows selecting a value from label-type tables that can be accessed when selecting an option for a button.
		Remember to first open the selection menu where this function will operate
     
- set_values_in_multiple_selection(
    self, 
    tab_name: Literal["Select values", "Exclude values"] = "Select values", 
    actions: list[str] = ["Clear", "Paste", "Take"]
):Performs the action of copying and pasting values in the multiple selection window.

- set_values_in_multiple_selection_file(
    self, 
    df: pd.DataFrame, 
    column: str, 
    address: str, 
    name: str, 
    clean_before: bool = True, 
    unique: bool = False, 
    tab_name: Literal["Select values", "Exclude values"] = "Select values"
):Performs the action of copying and pasting values from a file in the multiple selection window. This is done via a file to allow multiple bots to do it simultaneously without clipboard conflicts.


if you want know more about of **GuiObjects**, Explore [Sap Gui Objects](https://help.sap.com/docs/sap_gui_for_windows/b47d018c3b9b45e897faf66a6c0885a8/a2e9357389334dc89eecc1fb13999ee3.html).
