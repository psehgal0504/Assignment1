# Assignment1
cd ~
perl -MNet::FTP -e     '$ftp = new Net::FTP("ftp.ncbi.nlm.nih.gov", Passive => 1);
$ftp->login; $ftp->binary;
$ftp->get("/entrez/entrezdirect/edirect.tar.gz");'
gunzip -c edirect.tar.gz | tar xf -
rm edirect.tar.gz
builtin exit
/bin/bash
export PATH=${PATH}:$HOME/edirect >& /dev/null || setenv PATH "${PATH}:$HOME/edirect"
./edirect/setup.sh
echo "export PATH=\${PATH}:/home/psehgal/edirect" >> $HOME/.bashrc
more .bashrc
echo $PATH
esearch -db pubmed -query "Smad1" | efilter -query "osteogenic differentiation" | efetch -format abstract  > Smad1_1.txt
ls -la
vi Smad1_1.txt
pip install wordcloud --user
scp mask2.png psehgal@trgn.usc.edu:
wordcloud_cli --text Smad1_1.txt --imagefile wordcloudfinal.png --mask mask2.png --contour_width 3 --contour_color blue --background white
