# Functionality:

This library is designed to automate the creation of the scaffolding for an Angular component, complete with Jasmine test placeholders.

# Installation:
Start by installing the Yeoman generator using the following guide: http://yeoman.io/codelab/setup.html

Afterwards, install the 'generator-ngcomponent' using this command in your terminal:

```sh
$ npm install generator-ngcomponent -g
```

## Usage:

1. You may choose to create a `.yo-rc.json` file in the directory where the component will be generated. If not created, the file will be generated automatically. Here is an example:

    ```json
    {
      "generator-ngcomponent": {
        "parentModule": "parent.module",
        "company": "Company Name",
        "templateDir": "src/app/modules/{component.name}/templates/",
        "componentDir": "src/app/modules/{component.name}/components/",
        "specDir": "test/unit/modules/{component.name}/"
      }
    }
    ```
    
    - `parentModule`: Defines the default module name. You'll be prompted to provide a name when generating the module.
    - `templateDir`: States the directory where the template (.tpl.html) files for your component will be placed. Non-existent directories in the path will be created.
    - `componentDir`: Specifies the directory where the component (.component.js) files will be stored.
    - `specDir`: Indicates the directory where the Jasmine test (.spec.js) files for your component will be placed.
    - `{component.name}`: All instances of this string will be replaced by the actual component name.
    
2. Execute the command:

    ```
    $ yo ngcomponent
    ```
    
    You'll then be prompted to enter the following:
    - Component Name: Provide the component's name in camel case. The generator will automatically convert this to snake case where required.
    - Description: A brief description of what the component does.
    - Module Name: By default, this is derived from the "parentModule" parameter in yo.rc.json. The component will be added to this module. This is also true for the tests - the Jasmine test uses `beforeEach('moduleName');` to find the component.

## Generated Structure:

By default, the generator will create the following structure:

```
   shared/components/thing.js
   test/unit/components/thing.spec.js
   shared/templates/thing.tpl.html
```

## After Generation:

- Adjust `templateUrl` in `shared/components/thing.js` as needed.
- The generated Jasmine test spec will contain code reminding you to populate the tests. This is what the placeholder test looks like:

        it('should have tests', function(){
            expect(false).toBeTruthy();
        });