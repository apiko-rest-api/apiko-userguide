# Apiko Guide

Welcome to the Apiko Guide.

If you have any questions that are not covered in the following topics, please post your question on [StackOverflow.com](http://stackoverflow.com/) and tag your question with **Apiko**. You can also join the community chat at: https://gitter.im/Apiko-Rest-API/Lobby

* [Installation and setup](Installation%20and%20setup.md)
    - [Installing the CLI tool](Installation%20and%20setup.md#installing-the-cli-tool)
    - [First setup and run](Installation%20and%20setup.md#first-setup-and-run)
    - [Next run](Installation%20and%20setup.md#next-run)
    - [Testing endpoints](Installation%20and%20setup.md#testing-endpoints)
    - [What's next](Installation%20and%20setup.md#whats-next)
* [Configuration](Configuration.md)
    - [Apiko setup](Configuration.md#apiko-setup)
    - [Apiko Configuration](Configuration.md#apiko-configuration)
        - [Environments](Configuration.md#environments)
        - [Configuration options](Configuration.md#configuration-options)
            - [port](Configuration.md#port)
            - [prefix](Configuration.md#prefix)
            - [verbosity](Configuration.md#verbosity)
* [Custom endpoint handlers](Custom%20endpoint%20handlers.md#custom-endpoint-handlers)
    - [Apiko-specific properties](Custom%20endpoint%20handlers.md#apiko-specific-properties)
        - [res.success(dataObject)](Custom%20endpoint%20handlers.md#ressuccessdataobject)
        - [res.error(HttpStatusCode, 'CustomMessage', CustomErrorCode)](Custom%20endpoint%20handlers.md#reserrorhttpstatuscode-custommessage-customerrorcode)
        - [req.all](Custom%20endpoint%20handlers.md#reqall)
        - [res.body and res.status](Custom%20endpoint%20handlers.md#resbody-and-resstatus)
    - [Extending core endpoint handlers](Custom%20endpoint%20handlers.md#extending-core-endpoint-handlers)
    - [Defining custom handlers without developer UI](Custom%20endpoint%20handlers.md#defining-custom-handlers-without-developer-ui)
* [Documenting your API](Documenting%20your%20API.md)
* [Serving frontend with Apiko](Serving%20frontend%20with%20Apiko.md)
* [Updating Apiko](Updating%20Apiko.md)
    - [Updating the Apiko CLI](Updating%20Apiko.md#updating-the-apiko-cli)
    - [Updating the Apiko server](Updating%20Apiko.md#updating-the-apiko-server)
