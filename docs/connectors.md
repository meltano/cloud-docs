## Connector Maintainers

* **Official** -  Official connectors and tools are built, maintained, supported, and tested by Meltano.
* **Partner** - Partner connectors and tools are built, maintained, supported, and tested by a partner organization of Meltano, including consultancies and other vendors.
* **Community** - Community connectors and tools are built and maintained by the wider open source community.

## Connector Quality

* **Platinum** - Platinum connectors are built on the Meltano SDK and are maintained, supported, and tested by Meltano or our Partners. Additional SLAs are available for these connectors in Meltano Cloud. Contact us to learn more.
* **Gold** - Gold connectors are built on the Meltano SDK, are actively used by many Meltano Cloud and open source users, and have broad coverage of data and features.
* **Silver** - Silver connectors may be built on the Meltano SDK, but their open source and Meltano Cloud usage may be lower compared to a Gold connector.
* **Bronze** - Bronze connectors are not based on the Meltano SDK. We have some usage data for this connector in Meltano Core or Cloud.
* **No Data** - Connectors for which we have no usage data. They likely have not been tested and the repository maintainers may be unresponsive.


### Connector Quality Matrix

To give users a better understanding of the overall quality of a connector, we have the following matrix and guidance on attributes that affect the quality rating.

|         | SDK-Based | Usage Data    | Maintainer         | Repo Activity  |
|---------|-----------|---------------|--------------------|----------------|
| Gold    | Yes       | > 5 Projects  | Meltano or Partner | High           |
| Silver  | Possibly  | >= 1 Projects | Community          | Medium on Repo |
| Bronze  | No        | >= 1 Projects | Community          | Low            |
| No Data | No        | Unkonwn       | Community          | Unknown        |

<!-- Generated from https://www.tablesgenerator.com/markdown_tables -->

For all connectors we may apply feedback we get from the community or our judgement to adjust the quality indicator of a connector.

Please reach out to us to learn more about Platinum-level support for Gold connectors.

**Are these connectors production ready?**

Gold connectors are production ready. Silver connectors are very likely ready for production. Bronze connectors could be ready for production, but assessing them for your use case is recommended.

One additional factor is what stage of development the connector is in. We recommend [semantic versioning](https://semver.org/) for connector development. If a connector is at v1.0.0 or greater, then it is definitely production-grade. For connectors between versions 0.1.0 and 1.0.0, they could be production ready and a number of users could be using them actively. But it is worth considering your own use case and whether it has the streams and features you need. If the connector is <0.1.0 then it still in development and is likely not ready for production.
