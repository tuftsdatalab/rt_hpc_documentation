## Rclone

Rclone is a tool to manage files stored on cloud storage. Some examples of this are Box, Google Drive, Amazon, etc.. To connect Rclone to the cluster, 
you will need to install it on your local machine to set up your access token and then configure your Rclone on the cluster using this token.

## Rclone Installation

- To set up Rclone on your local machine follow the instructions for your machine type:

!!! info "[Rclone Installation](https://rclone.org/install/){:target="_blank" rel="noopener"}"

## Rclone Configuration

- On your local machine navigate to your terminal/command prompt and enter the following command to authorize the connection to the clound storage of your choice. Here we will demonstrate how to connect to Box:

```
rclone authorize "box"
```

- Now the following text will pop up along with a web browser with instructions to enter your credentials. Follow the instructions and take the SECRET_TOKEN they provide and paste it into your terminal/command prompt whent prompeted:

```
If your browser doesn't open automatically go to the following link: http://127.0.0.1:53682/auth
Log in and authorize rclone for access
Waiting for code...
Got code
Paste the following into your remote machine --->
SECRET_TOKEN
<---End paste
```

- Now on navigate to the cluster (if you do not know how check out [these instructions](https://bionomad.github.io/tuftsTutorials/hpc-user-guide/navigate-to-cluster/)) and enter the following command:

```
module load rclone
```

- Now we will start creating a remote file:

```
rclone config
```

- You will be prompted to create a remote file:

```
No remotes found, make a new one?
n) New remote
s) Set configuration password
q) Quit config
n/s/q> n
name> remote
Type of storage to configure.
Choose a number from below, or type in your own value
[snip]
XX / Box
   \ "box"
[snip]
Storage> box
Box App Client Id - leave blank normally.
client_id> 
Box App Client Secret - leave blank normally.
client_secret>
Box App config.json location
Leave blank normally.
Enter a string value. Press Enter for the default ("").
box_config_file>
Box App Primary Access Token
Leave blank normally.
Enter a string value. Press Enter for the default ("").
access_token>

Enter a string value. Press Enter for the default ("user").
Choose a number from below, or type in your own value
 1 / Rclone should act on behalf of a user
   \ "user"
 2 / Rclone should act on behalf of a service account
   \ "enterprise"
box_sub_type>
Remote config
Use web browser to automatically authenticate rclone with remote?
 * Say Y if the machine running rclone has a web browser you can use
 * Say N if running rclone on a (remote) machine without web browser access
If not sure try Y. If Y failed, try N.
y) Yes
n) No
y/n> n
For this to work, you will need rclone available on a machine that has
a web browser available.

For more help and alternate methods see: https://rclone.org/remote_setup/

Execute the following on the machine with the web browser (same rclone
version recommended):

	rclone authorize "box"

Then paste the result below:
result>
```

- Now, in the result field enter the SECRET_TOKEN you got on your local machine:

```
result> SECRET_TOKEN
--------------------
[acd12]
client_id = 
client_secret = 
token = SECRET_TOKEN
--------------------
y) Yes this is OK
e) Edit this remote
d) Delete this remote
y/e/d>
```

!!! success 
    Congrats! You have Rclone configured on the Tufts HPC Cluster!

## Rclone Cluster Use

- To examine files in your remote storage you can use the following command (assuming the name of your remote is `box`):

```
rclone ls box:/
```

- To copy those files to your location on the cluster you can use (assuming the name of your remote is `box`):

```
# to download a file to the cluster
rclone copy box:/path/to/file .

# to upload a file from the cluster to the cloud storage
rclone copy filename box:/path/to/desitination/
```

- To learn more about the different types of Rclone commands use the help option:

```
rclone help
```

## References

!!! abstract ""

    1. [Rclone](https://rclone.org/)
