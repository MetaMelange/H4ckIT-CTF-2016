#forensics_1n51d3r'5_j0b - Canada

#####Trivia
This challenge was the challenge with the best work/points ratio. It gave 300 points for one grep command.

#####The 'Challenge'
When we unzipped the file we got the following 2 files: <br \>
out.txt - some txt file with a lot of links, especially some pr0n stuff <br \>
parse - A Go Binary

So i made a grep over all the strings in the 2 files: <br \>
`strings * | grep 'h4ck1t'`

In the Go Binary I found the flag via grep.

#####The Flag

**h4ck1t{T0mmy_g0t_h1s_Gun}**


##### Background of this 'hard' challenge

The creator of this challenge told me it was his mistake. He made a Go binary and it was not his 
intention that you could just grep out the flag.
