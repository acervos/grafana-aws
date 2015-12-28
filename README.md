<h1 align="center">Grafana</h1>
[Grafana](http://grafana.org) is the basis for all our metrics that come from our various services and applications.  It offers a rich interface to analyse and view metrics and stats from the database, InfluxDB, or cloudwatch

### Using Grafana

There are many features of Grafana that can be found in the [documentation](http://www.grafana.org), however looking at existing dashboards is advised.

### Grafana Admin

Grafana comes with a login system, this means that anyone can view Grafana without changing anything.  If you want to make a change, simply create an account.  The login does not require activation, so you can start making changes right away, you can also login via Github credentials.

### Saving Dashboards

The Grafana interface allows you to save dashboards.  These dashboards are stored in RDS using Postgres, this means when Grafana restarts, all you changes are still present.

### Configuration Options

All options for Grafana are stored in the grafana.ini.

# Setup on AWS

### Create Security Group

Upload the RDS security group template

### Create the RDS instance

Upload the RDS template, use the RDSSecurityGroup resource you just created

### Create the Grafana instance

Upload the main template, use the RDSComponentSecurityGroup resource you just created.  You will be asked for a grafana.ini URL, this is required as you will need to put your RDS Postgres details into a config file.  

There is a sample config file in this repo, so you can either fork this repo or create a private gist/place in S3 to use with wget.  This will overwrite the default config file provided by Grafana, there are a lot of config options for Grafana, see [the docs for details](http://docs.grafana.org/installation/configuration/)
