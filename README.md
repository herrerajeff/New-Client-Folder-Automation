# Automating the creation of the 'best folder structure for design projects'

Folder Structure taken from: [Matt D. Smith's "BEST FOLDER STRUCTURE FOR DESIGN PROJECTS" video](https://www.youtube.com/watch?v=uZ9om-iogQE)

## What it does

Easy.
You input your client's name, and the type of project, and the following folder structure will be automatically created for you:

![Terminal Window](/Screenshots/terminal.png?raw=true)

![Folder Structure](/Screenshots/finder.png?raw=true)

## Getting Started

There are two options:

### Add the function to your Bash Scripts (My Preferred Method)

Open Terminal & edit your .bashrc file:

```
$ sudo nano ~/.bashrc
```

Copy & paste the newclient function then press Control ⌃+O with Control ⌃+X to exit:

```
newclient(){
    clear
    echo "Please enter your client name and press [ENTER]:"
    read name
    printf "\nPlease enter the project type and press [ENTER]:\n"
    read project
    client_name="$name"
    project_type="$project"
    sleep 0.5
    printf "\n__________________________\nNavigating to your Clients folder\n\n"
    sleep 0.5
    printf "__________________________\nCreating Directory\n\n"
    sleep 0.5

    ########################################
    #                                                                           #
    #       Edit this path to your own client folder        #
    #                                                                           #
    #######################################

    cd /Users/jeffreyherrera/Library/Mobile\ Documents/com\~apple\~CloudDocs/_Clients

    if [[ -d "$client_name" ]]; then
        printf "\n*********************************\n☠  Dang. ☠\n\nYou already have a client by that name.\nTry running this again using a different client name\n\n\nhint: use the up arrow and press enter for it to re-run quickly\n\n\n"
        exit 1
    else

        ####################################################################
        #                                                                                                                                    #
        #       This makes your folder structure...feel free to edit with your requirements         #
        #                                                                                                                                   #
        ###################################################################

        sudo mkdir -p "$client_name"/Case\ Study "$client_name"/Contracts  "$client_name"/Projects/$project_type/Assets "$client_name"/Projects/$project_type/Assets/Brand\ Guidelines "$client_name"/Projects/$project_type/Assets/Images "$client_name"/Projects/$project_type/Assets/Fonts "$client_name"/Projects/$project_type/Design "$client_name"/Projects/$project_type/Design/Sketch "$client_name"/Projects/$project_type/Design/Illustrator "$client_name"/Projects/$project_type/Design/InDesign "$client_name"/Projects/$project_type/Review "$client_name"/Research

        sleep 0.5
        printf "\n*********************************\n 🚀  Congrats! 🚀 \n\nNew client $client_name created with project type $project_type.\n\n"
        cd ~
    fi
}

```

Reload after saving changes:

```
. ~/.bashrc
```

### Download 'new-client.sh' file from this repo
