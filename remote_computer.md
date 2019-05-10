# Accessing Remote Computer With Command Line Interface

(also see Ch. 20 in Haddock and Dunn "Practical Computing for Biologists")

Although the University of Surrey tutorial is a very good introduction to the command line / terminal environment, one section that it lacks is how to interact with computers and/or files remotely, either sitting across the room or on the other side of the world. Let’s explore a few standard ways this can be done.

There are (at least) two programs that can be used to retrieve a file from a web site via the CLI. These are wget and curl. We will be using curl. Mac OS X and Windows 10 Ubuntu have it installed by default and it can be easily added to other Linux systems through the Package Manager.

To use curl from the CLI, use the following command syntax:

`curl WEB_ADDRESS_OF_THE_FILE_THAT_YOU_ARE_DOWNLOADING > NAME_YOU_WANT_FOR_THE_DOWNLOADED_FILE`

For example, to download a PDF file named "Santos2006MolEcol.pdf" from a lab’s website (e.g., http://www.auburn.edu/~santosr/pdf/), you could do the following:

`curl http://www.auburn.edu/~santosr/pdf/Santos2006MolEcol.pdf > Santos2006.pdf`

Now that we know how to download files from a web site, how can we do the same thing with a file sitting in a user's account on another computer? More generally, to connect to a remote UNIX/Linux computer in a secure fashion, the program ssh (e.g., secure shell) is used:

`ssh ACCOUNT_NAME@IP_ADDRESS_OF_COMPUTER`

After you type in the command and hit "Enter", you will be presented with a couple of questions, one of which is the password for the account name that you are connecting to. Type in the password (it will not show up on the screen for security purposes), hit "Enter", and you will now be able to access the remote computer via the CLI as if your were sitting in front of it.

Let's practice connecting to a remote computer via ssh by doing the following:

`ssh student@the santos lab.dynu.net`

Accept (say yes to) any host authenticity prompt and then enter (e.g. copypaste from below) the password that you received via email (which will not be visible ).

When finished, you can disconnect by typing `exit`, `logout` or `ctrl-d`. It should be noted that ssh will only work to connect to computers with "Remote Login and File Sharing" enabled.

To copy files in a secure fashion between UNIX/Linux computers without logging in, we can use the program scp (e.g., secure copy) in the following way:

  To send a file to a remote computer:
  
  `scp FILE_YOU_ARE_SENDING ACCOUNT_NAME@IP_ADDRESS_OF_RECEIVING_COMPUTER:WHERE_YOU_WANT_TO _PUT_IT_AND_ITS_NAME` (NOTE THE SPACE AFTER THE FILE NAME IN THE COMMAND ABOVE AS WELL AS THE @ SIGN AND COLON)

  To retrieve a file from a remote computer: scp ACCOUNT_NAME@IP_ADDRESS_OF_HOST_COMPUTER:FILE_LOCATION_AND_ITS_NA ME YOUR_CHOSEN_FILE_NAME_ON_LOCAL_COMPUTER (NOTE THE @ SIGN, COLON AND SPACE BEFORE YOUR CHOSEN FILE NAME)

How useful is this? Imagine that you are at a meeting and something has happened to the pdf file that you were going to use for your slides. Let's use scp to retrieve a copy of the original from our office (remote) computer by doing the following:

`scp student@the santos lab.dynu.net:homework/slides.pdf Newslides.pdf`

Enter the password (or copypaste) and note again that the password won’t be visible for security reasons and the file will be automatically downloaded to the current directory that you are in. Now open the Newslides.pdf to make sure it’s fine and you are ready to give your talk. This is just one example; once you get comfortable with using `scp` , you'll never need a USB flash drive to transfer files between UNIX/Linux computers again.
