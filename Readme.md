# SAP GUI SCRIPTING

This project offers an abstraction over the SAP GUI Scripting API, facilitating interaction with the SAP GUI system. It allows navigation among different SAP transactions and downloading and transforming information exported from these transactions.

**Key Features:**
- **Automated Logging:** Performs records in SAP quickly and easily, minimizing the risk of manual errors.
- **Simplified Navigation:** Enables agile movement between different SAP transactions, optimizing workflow.
- **Data Download and Transformation:** Exports information from SAP and transforms it for use in other applications or analysis, facilitating data-driven decision-making.


## Tabla de Contenidos

1. [Installation](#installation)
2. [Basic Usage](#use)
5. [Recomendations](#recomendations)
3. [Contribution](#contribution)
4. [License](#license)
5. [Contact](#contact)


## Installation


Remember create your 'venv'

```bash
python -m venv venv

venv/Scripts/Activate

pip list

python.exe -m pip install --upgrade pip

pip install sap-gui-library
```

The second step is to use the following command if you see the library all is ok

```bash
pip list

>> ...
>> sap-gui-library   version
>> ...
```

You are ready to use sap library, in your proyects

## Use

The following example demonstrates the most basic and simple usage of this project. For more detailed documentation, please visit [sap_gui_library documentation](https://github.com/Chaparroo/sap-gui-library/tree/master/docs).


```python
from sap_gui_library import SapGui,Transaction,DataProcess
```

- ### How open sap?

    ```python
    sap_instance=SapGui(
        conection="our conection",
        user="user",
        password="password"
    )
    session=sap_instance.get_session()
    ```

- ### Basic proccess in transaccion

    ```python
    COOISPI=Transaction(
        session=session, # or sap_instance.get_session()
        code="COOISPI")
    COOISPI.start_transaction()
    COOISPI.select_variant(
        variant_author="USER",
        variant_name="VARIANT"
    )
    ...
    #COOISPI.session.FindById("id").text=""# example
    #COOISPI.session.FindById("id").press()# example2
    COOISPI.run_transaction()
    COLUMNS_NAMES=COOISPI.get_column_names()
    COOISPI.export_in_shell_or_grid()
    COOISPI.select_export_and_download(
        address=address,
        name="name_file"
    )
    ```

- ### Data transformation

    ```python

    DATA=DataProcess(
        address_file=os.path.join(address,"name_file.csv")
        ...
    )
    DATA.edit_file(
        generic_name_columns=COLUMNS_NAMES,
        ...
    )
    df=DATA.get_df()
    ```

## Recomendations
The following recommendations are for interacting with SAP in Python development:

- ### SAPGUI version

   A version of SAPGUI **770 or higher is required.**

- ### Scripting Tracker
    This tool helps identify all the elements (objects) we can interact with in each SAP session. You can download it from the official page using this link: [Scripting Tracker](https://tracker.stschnell.de/).
    If you want more information about the tool, you can find it on the official SAP [forum](https://community.sap.com/t5/technology-blogs-by-members/scripting-tracker-development-tool-for-sap-gui-scripting/ba-p/13282144).

    <img title="Visual Scripting Tracker" src="https://community.sap.com/legacyfs/online/storage/blog_attachments/2014/11/tracker001-1.jpg" height=250>
    

 - ### SAPGUI Accessibility - Scripting

    
    To interact with SAP in a more fluid and simple way, there are several settings that should be adjusted beforehand:

    - In the options tab:
        - option 1
        <img alt="Source: SAP Help Portal, SAP Business One documentation" title="Accessing options" src="https://help.sap.com/doc/63bd20104af84112973ad59590645513/800.08/en-US/loio731c5ff4610441c2ada36826814cb79a_LowRes.png" >

            <img alt="Source: SAP Help Portal, SAP Business One documentation" title="Accessing options" src=" https://help.sap.com/doc/63bd20104af84112973ad59590645513/800.08/en-US/loio3f85028df9544adab53ceda6c5e457dd_LowRes.png" >

       
        - option 2
        <img alt="Source: SAP Help Portal, SAP Business One documentation" title="Accessing options" src="https://help.sap.com/doc/63bd20104af84112973ad59590645513/800.08/en-US/loio52365e4463d94aa291f96a0e2e5cb98d_LowRes.png" >
        

    - Under Accessibility and Scripting --> Scripting --> enable the "Enable scripting" option and disable the other three options so that you don't get notified every time a script runs.

       <img  alt="Source: SAP Help Portal, SAP Business One documentation" title="Enable scripting" src="https://help.sap.com/doc/63bd20104af84112973ad59590645513/800.08/en-US/loio6cc6d83860df4300992c8898a1e89a99_LowRes.png" height=150 >

    - Before going to the Accessibility tab and enabling the "Use accessibility mode" option, we need to change the SAP theme or visual style to "SAP Signature Theme." Once this is done, you can go back to Accessibility and Scripting --> Accessibility --> and enable the "Use accessibility mode" option.

        <img alt="Source: SAP Help Portal, SAP Business One documentation" title="Use accessibility mode" src="https://help.sap.com/doc/63bd20104af84112973ad59590645513/800.08/en-US/loio8412c7f8ff4241c9ba44d63774a8faca_LowRes.png" height=150>
    

- ### SAPGUI Web API

    If you want to dive deeper into the attributes and methods available for each object in SAPGUI, you can check the [documentation](https://help.sap.com/docs/sap_gui_for_windows/b47d018c3b9b45e897faf66a6c0885a8/a2e9357389334dc89eecc1fb13999ee3.html), which comes from the official SAP site.


## Contribution

Thank you for your interest in contributing to this project! Here's how you can do it:

- ### 1. Fork the Repository
    First, fork the repository by clicking the "Fork" button at the top of the repository page.

- ### 2. Create a Branch
    Clone your fork to your local machine and then create a new branch for your work. Name your branch according to the feature or bug you're working on:

    ```bash
    git checkout -b your-branch-name
    ```
- ### 3. Make Your Changes
    Make the changes you believe are necessary.

- ### 4. Commit Your Changes
    Once you've made your changes, commit them with a clear description of what you've done:
   ```bash
    git add .
    git commit -m "Clear description of the changes"
    ```

- ### 5. Push Your Branch
    Push your changes to the remote repository:
    ```bash
    git push origin your-branch-name
    ```
- ### 6. Create a Pull Request
    Go to the original repository on GitHub and click the "New Pull Request" button. Clearly explain the changes you've made and why they should be merged.

## License
- MIT License

## Contact

If you have any questions, suggestions, or feedback, feel free to contact us:


- **LinkedIn:** [Felipe Lopez](https://www.linkedin.com/in/lopez-chaparro/)
- **GitHub Issues:** Please report issues or feature requests [here](https://github.com/Chaparroo/sap-gui-library/issues)





