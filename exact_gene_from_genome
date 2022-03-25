#-*-coding:utf-8-*-

'''
Name: exact-genes.py
Objective: To extract a sequence at a given location
Author: Wang Binzhong
Date: 2022-03-24
Comment: The script needs big memory depending on genome fasta file.
Please confirm it.
'''

import os



def exact_gene(fr, chromosome, start, end,fw_name):
    with open(fr,'r') as f:
        sp = f.read().split('>')
        string = '\n'
        
        #find sequence name, cut out a long sequence containing sequence name, then strip ATGC
        name = sp[chromosome][:10].rstrip('ATGC')
        name_length = len(name)    
        start = start + name_length
        end = end + name_length
        #count '\n' 
        count_n = sp[chromosome][start:end].count(string)
        #write sequence
        with open(fw_name + ".fa","w") as fw:
           name = name.strip("\n")
           seq = ">%s %d:%d\n%s" % (name, start, end, sp[chromosome][start:end-count_n])
           fw.write(seq)   
        fw.close()
        
if __name__ == '__main__':

    #change into work directory which contains genome fasta file
    os.chdir(r'K:\01-Genome_blastdb\Acipenser_sinensis_ont')
    #read genome fasta file
    fr = 'A.sinensis.ONT.Hic.bk.fasta'
    #chromosome number
    chromosome = 1
    #start position 
    start = 49037933
    #end position 
    end = 49038959
    #up to you to name the file name
    fw_name = "marker-%d-%d" % (start, end)
    #run the def
    exact_gene(fr, chromosome, start, end,fw_name)
