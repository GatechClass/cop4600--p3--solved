# cop4600--p3--solved
**TO GET THIS SOLUTION VISIT:** [COP4600 -P3 -solved](https://mantutor.com/product/cop4600-p3-solved/)


---

**For Custom/Order Solutions:** **Email:** mantutorcodes@gmail.com  

*We deliver quick, professional, and affordable assignment help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;77377&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;2&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (2 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;COP4600  -P3  -solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (2 votes)    </div>
    </div>
File Systems

Overview

Your cover in the Lizard Legion was blown, and you’ve been revealed as a double agent and driven out! It was all very “James Bond”, if you do say so yourself, and what a daring underground helicopter escape it was… but you feel lucky to have escaped with your skin. (Literally… they would have used you to make a “human suit”!) Now that you’re back on the “outside”, you’ve been tasked with creating a scheme to allow remaining resistance fighters still within the Lizard Legion to clandestinely move information back to your organization without raising suspicion. As of late, members of the Lizard Legion have discovered the PC classic “DOOM”, and it has become all the rage to build new mods for it at headquarters, so your team has decided to use mods for this title as a vehicle for exfiltration. By burying encrypted bits within textures and other game data blocks, information can be hidden within innocuous “WAD” (Where’s All the Data) files.

In this project, you will implement a userspace filesystem daemon using the FUSE (Filesystem in UserSpacE) API to access data in WAD format, the standard used in a number of classic PC game titles (including DOOM and Hexen). In this critical early prototype, you have been tasked with implementing read-only access to files and directories within the WAD files as a proof-of-concept. As such, you will need to implement open, read, and release functionality for both files and directories within your FUSE-based program. We, as your comrades-inarms battling the Reptilian invasion, will provide sample WAD files to demonstrate the functionality of your implementation. (The resistance is counting on you!) The resistance uses university courses as cover for standard operations, so you’ll submit the project via Canvas.

Structure

The project is broken into three main parts:

1) Develop a library to read a WAD file and create a directory and file structure from it.

2) Implement a userspace daemon (via FUSE) to access the directory structure once mounted.

3) Test your implementation by navigating the mounted directory and examining the names and file contents.

While exact implementation may vary, the daemon’s parameters must match those laid out in this document, and the directory structure, naming, and file contents must be properly presented via the filesystem.

File and Directory Requirements

Your daemon must implement, at a minimum, the following filesystem functions to provide read-only access:

1) Retrieving file and directory attributes

2) Opening, reading, and releasing files

3) Opening, reading, and releasing directories

Directories should be only executable and readable for all users, while files should be only readable by all users.

File Format

The WAD file format contains information in three sections: the header, which gives basic layout information, the descriptors, which describe elements in the file, and the lumps, which contain the data themselves. NOTE: all numbers are in little-Endian format and, where applicable, are designated in bytes!

File Header

The header contains the file magic, descriptor count, and location (offset) of the descriptors in the file:

The magic for a wad file is usually ASCII and always ends in the suffix “WAD” (e.g., “IWAD” or “PWAD”).

Descriptors

The file’s descriptors contain information about elements in the WAD file – its file offset, length, and name:

Some elements have a length that is zero. These “marker” elements will be interpreted by the daemon as directories and should be displayed accordingly in the filesystem (see below).

Lumps

Elements in the WAD format are stored as “lumps” described by the descriptors. These lumps will be represented in the filesystem by the daemon as individual files that can be opened, read, and closed.

Marker Elements

There are two primary types of marker elements in WAD files, each of which should be interpreted as directories by our daemon. The type includes map markers and namespace markers.

Map marker names are of the format “E#M#”, where # represents a single decimal digit (e.g., “E1M9”). They are followed by ten (10) map element descriptors. The elements for the next 10 descriptors should be placed inside of a directory with the map’s name.

Namespace markers come in pairs. A namespace’s beginning is marked with a descriptor whose name has the suffix “_START” (e.g., “F1_START”), and its ending is marked with a descriptor whose name has the suffix “_END” (e.g., “F1_END”). Any descriptors for elements falling between the beginning and ending markers for a namespace should be placed within a directory with the namespace’s name (e.g., “F1”).

For example, the following descriptors, in order, in the descriptor list, should result in this organization:

Offset Length Name  Directory Structure

0 0 F_START

0 0 F1_START F

F1

E1M1

THINGS

LINEDEFS

SIDEDEFS

VERTEXES

SEGS

SSECTORS

NODES

SECTORS

REJECT

BLOCKMAP LOLWUT

67500 0 E1M1

67500 1380 THINGS

68880 6650 LINEDEFS

75532 19440 SIDEDEFS

94972 1868 VERTEXES

96840 8784 SEGS

105624 948 SSECTORS

106572 6608 NODES

113180 2210 SECTORS

115392 904 REJECT

116296 6922 BLOCKMAP

42 9001 LOLWUT

0 0 F1_END

0 0 F_END

Library

Your library will contain a class to represent WAD data as described in this section.

Wad Class

The Wad class is used to represent WAD data and should have the following functions. The root of all paths in the WAD data should be “/”, and each directory should be separated by ‘/’ (e.g., “/F/F1/LOLWUT”).

public static Wad* loadWad(const string &amp;path)

Object allocator; dynamically creates a Wad object and loads the WAD file data from path into memory. Caller must deallocate the memory using the delete keyword.

public string getMagic()

Returns the magic for this WAD data.

public bool isContent(const string &amp;path)

Returns true if path represents content (data), and false otherwise.

public bool isDirectory(const string &amp;path)

Returns true if path represents a directory, and false otherwise.

public int getSize(const string &amp;path)

If path represents content, returns the number of bytes in its data; otherwise, returns -1.

public int getContents(const string &amp;path, char *buffer, int length, int offset = 0)

If path represents content, copies as many bytes as are available, up to length, of content’s data into the preexisting buffer. If offset is provided, data should be copied starting from that byte in the content. Returns number of bytes copied into buffer, or -1 if path does not represent content (e.g., if it represents a directory).

public int getDirectory(const string &amp;path, vector&lt;string&gt; *directory)

If path represents a directory, places entries for immediately contained elements in directory. The elements should be placed in the directory in the same order as they are found in the WAD file. Returns the number of elements in the directory, or -1 if path does not represent a directory (e.g., if it represents content).

Daemon Command &amp; Parameters

Your daemon should have name wadfs and should accept at a minimum two parameters – the target WAD file and mount directory. For example, this command should mount TINY.WAD in /home/reptilian/mountdir…

$ ./wadfs TINY.WAD /home/reptilian/mountdir $

…and this should result from executing the ls command to show part of its contents:

$ ls /home/reptilian/mountdir/F/F1 -al total 0 dr-xr-xr-x. 2 root root 0 Jan 1 1970 . dr-xr-xr-x. 2 root root 0 Jan 1 1970 .. dr-xr-xr-x. 2 root root 0 Jan 1 1970 E1M1 -r–r–r–. 2 root root 9001 Jan 1 1970 LOLWUT

Your daemon should run in the background. Do not hard-code the debug flag (-d)!

Building with FUSE

FUSE is a userspace filesystem API that is supported directly by the Linux kernel. It allows userspace programs to provide information to the kernel about filesystems the kernel cannot interpret on its own.

Installation &amp; Setup

To use the FUSE library, you will need to install it within Reptilian and change the FUSE permissions:

$ sudo apt install libfuse-dev

$ sudo chmod 666 /dev/fuse

NOTE: if you reboot the virtual machine, you will need to re-add the FUSE permissions, as they will be reset!

Build Directives

In order to build programs using the FUSE library system, you will need to specify the file offset bits as 64 and identify the FUSE version. We recommend specifying FUSE version 26 (though this is optional):

$ g++ -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 myproggy.cpp -o myproggy -lfuse

Submissions

You will submit the following at the end of this project:

 Report (p3.txt) in man page format on Canvas, including link to unlisted screencast video

 Compressed tar archive (wad.tar.gz) for libWad library and wadfs daemon on Canvas

Report

Your report will explain how you implemented the daemon, including your general architecture / program structure. It must include an explanation of how you represent the WAD file elements as a directory structure in memory, as well as how this structure was utilized in the daemon when running. It will include a description of how testing was performed along with any known bugs. The report should be no more than 500 words, cover all relevant aspects of the project, and be organized and formatted professionally – this is not a memo!

Screencast

In addition to the written text report, you should submit a screencast (with audio) walking through the daemon you wrote to provide the filesystem interface, describing your primary functions and structures (~5 minutes).

Compressed Archive (wad.tar.gz)

Your compressed tar file should have the following directory/file structure:

To build the library and daemon, we will execute these commands:

$ tar zxvf wad.tar.gz $ cd libWad

$ make

$ cd wadfs

$ make $ cd ..

To run your daemon, we will execute this command:

$ ./wadfs/wadfs somewadfile.wad /some/mount/directory

To build another program using your library, we will execute this command:

$ c++ -o program_name sourcefile.c -L ./libWad -lWad

Please test that your daemon builds and executes before submission! It is strongly recommended that your daemon utilize your library file for ease of testing. If your daemon does not compile it will result in zero credit (0, none, goose-egg) for the functionality portion of the project.

Helpful Links

You may find the following resources helpful when reading about how to implement a FUSE daemon:

https://www.cs.nmsu.edu/~pfeiffer/fuse-tutorial/html/ https://engineering.facile.it/blog/eng/write-filesystem-fuse/ http://slade.mancubus.net/index.php?page=about
