---
title: Basic Molecular docking
author: ct
layout: post
categories:
  - Molecular docking
tags:
  - Molecular docking
---

### ���׿��ӻ�

���ǹ۲����һ���ֱ���Ϊ2����X-�������侧��ṹ(PDB ID: [1HSG](http://www.rcsb.org/pdb/explore/explore.do?structureId=1HSG))��չʾ����HIV-1����ø��ҩ�������Τ([indinavir](http://en.wikipedia.org/wiki/Indinavir))�����һ��Ĺ������[`PyMOL`](https://pymolwiki.org/index.php/Practical_Pymol_for_Beginners)�����۲�HIV-����ø�����λ���ҩ������Ľṹ��

* ����HIV-1����ø��PDB�ṹ(https://files.rcsb.org/download/1HSG.pdb)���洢��һ���������ĵ�Ŀ¼�¡�
* ����PyMOL
* ѡ��`File`-`Open`-`1hsg.pdb`

![file_open_visual.png]({{ site.imgurl }}/docking/file_open_visual.png)

* �����������е�ͼ�����Ҳ�Ķ��������壬��`all`��`H`��`Hide: everything`����ʱ��ĻӦ�������һƬ��

![all_hide_everything.png]({{ site.imgurl }}/docking/all_hide_everything.png)

* ��ʾ���ף����Ҳ�Ķ��������壬��`1hsg`��`S`�У�ѡ��`cartoon`չʾ��Ȼ����`C`�а�`chain`��ɫ����ʱ���Կ���һ��ͬԴ�������չʾ��

![1hsg_cartoon_chain.png]({{ site.imgurl }}/docking/1hsg_cartoon_chain.png)

* ��ɫ����ҩ��`indinavir`����л�������Ϊ`MK1`,�����Ϣ����������PDB��վ���Ӳ鿴����������ͼ��ʾ��

![ligand_indinavir_mk1.png]({{ site.imgurl }}/docking/ligand_indinavir_mk1.png)

��PyMOL�������д�����`select indinavir, resn MK1`������ͼ��ʾ

![get_ligand_using_select.png]({{ site.imgurl }}/docking/get_ligand_using_select.png)

�س��󣬻ῴ��������ͼ��ʾ

![ligand_indinavir_mk1_show_1.png]({{ site.imgurl }}/docking/ligand_indinavir_mk1_show_1.png)

* ��ʾ���壬���Ҳ�Ķ��������壬��`indinavir`��`S`�У�ѡ��`stick`չʾ����ѡ��`C`һ�ֲ�ͬ����ɫ������Ļû����ͼ�������꣬ȡ��ѡ��

![lgand_show.png]({{ site.imgurl }}/docking/lgand_show.png)

* PyMOL����������ס����ƶ���ת����ס�Ҽ��ƶ��Ŵ󣬰�ס�м��ƶ����۲���λ�����ڵ�λ�á�

* ��ʾˮ���ӣ�ˮ���ӵĲл�����Ϊ`HOH`����������`select H2O, resn HOH`����ˮ���ӡ�Ȼ��ѡ��`S`-`spheres`,`C`-`red`��������`set sphere_scale, 0.2`����ˮ��Ĵ�С��

* �洢, ������������`png E:/docking/1shg.png`���浱ǰ�����

![1hsg.png]({{ site.imturl }}/docking/1hsg.png)

### ׼��docking��Ҫ������(protein)������(������)

Docking�㷨��Ҫÿ��ԭ�Ӵ��е�ɲ�����Ҫ���ԭ�ӵ����ԡ���Щ��Ϣ��PDB�ļ��в����ڡ�������Ҫ������һ��[`PDBQT`](http://autodock.scripps.edu/faqs-help/faq/what-is-the-format-of-a-pdbqt-file)�ļ�����������Ϣ��PDB�ļ��е�ԭ��������Ϣ����һ���ض��ڡ���������docking�������ǻ���Ҫ�����������Щ���ǿ�����ת�ġ�������Щ������ͨ�����[`AutoDock Tools (adt)`](http://mgltools.scripps.edu/)����ɡ�

Docking algorithms require each atom to have a charge and an atom type that describes its properties. However, the PDB structure lacks these. So, we have to prep the protein and ligand files to include these values along with the atomic coordinates. Furthermore, for flexible ligand docking, we should also define ligand bonds that are rotatable. All this will be done in a tool called AutoDock Tools (adt).

#### ׼�����嵰��

1. PDB�ļ�(1hsg.pdb)�а����˵��ס������ˮ���ӣ�������ȡ�����׵����꣬���Թؼ���`ATOM`��ͷ���С�ÿһ���������Թؼ���`TER`��ͷ������Ϊ��ֹ�С�

  * ��windows�£����ǿ����ֶ�ѡ�񣬻�������Excel��ɸѡ���ܡ�
  * ��Linux�£�ʹ������`egrep "^(ATOM|TER)"` 1hsg.pdb >1hsg_prot.pdb

2. ����AutoDockTools
  
  * windowsֱ��˫��ͼ��Ϳ�
  * linux����ʹ������`adt &`

3. ���ص��׷��� `File`-`Read MOlecule`-'1hsg_prot.pdb'��
  
  * ADT�а�ס����϶���ת���ӽṹ������м����������ţ���ס�ʼ��ƶ�����λ�á�

4. ����չʾ��ʽ��`Color`-`By Atom Type`-`All Geometries`-`OK`��

5. ����ṹ��ͨ��ȱ����ԭ�� (��Ϊ��ԭ�ӵ����٣������Ӻ˶Ե�����������������˺��Ѷ�λ�������<http://www.uh.edu/~chembi/ChemSocRev_Jones_critical.pdf>)��������docking�����У���ԭ�ӣ������Ǽ�����ԭ�ӶԼ��㾲�������Ǳ���ġ����������Ҫ�����׼�����ԭ�ӣ�`Edit`-`Hydrogen`-`Add`-`Polar only`-`OK`(֮����ѡ��`Polar only`����Ϊ`vina`�Ĺٷ���Ƶ��������ôѡ���)����ʱ��ԭ�ӻ��԰�ɫ������ʽ���֡�

<figure class="half">
	<img src="{{ site.imgurl }}/docking/1hsg_prot_no_H.png" alt="1hsg_prot_no_H.png">
	<img src="{{ site.imgurl }}/docking/1hsg_prot_with_H.png" alt="1hsg_prot_with_H.png">
	<figcaption>������ԭ��ǰ���󣩺ͺ��ң����׽ṹ��ʾ</figcaption>
</figure>

6. �洢�Ե��׵�ÿ��ԭ���������޸ĺ�ԭ�����ͣ�`Grid`-`Macromolecule`-`Choose`,ѡ��`1HSG_protein`-`Slect Molecule`��ADT��ϲ��Ǽ�����ԭ�ӣ�ʵʩ�ı䲢��ʾ����`Save`-`1hsg_prot.pdbqt`�����ļ����鿴������У��ֱ�Ϊÿ��ԭ�ӵĵ��������͡�
  
  * `1hsg_prot.pdbqt`Ϊֻ���˼�����Ľ��
  * `1hsg_prot_all_h.pdbqt`Ϊ����������Ľ��
  
  �������ļ�������������ͬ������������Ƕ�docking��Ӱ�죬�ᷢ��û��Ӱ�죬�������������ļ�һģһ����

7. �������϶��������ϵ�3D�����ռ䡣����������Ȳ�֪�����λ�㣬���ǿ��Զ���һ�����Ӱ����������׻������һ���ض�����`Grid`-`Grid box`�����ڵ����ϻ���һ�������壬������һ���������ڵ������У���ק�̶��߲鿴������ı仯��

����������У�����֪�����λ�㣬��ѡȡ����Ϊ���ĵ�һ��С�ռ䡣����`Spacing (angstrom)`Ϊ`1`�� (��ʵ����һ������ϵ��)�������ǵ����Ĺ����У����Կ������������ֵ�ı��������Ҳ���Ŵ��ˡ�������������`x,y,z center`Ϊ`16,25,4`,`number of points in (x,y,z)-dimension`Ϊ`30,30,30`�������������õ���Щ�㡣

�ص�grid��protein��`Grid Options`-`File`-`Close w/out saving`; `Edit`-`Delete`-`Delete Molecule`-`1hsg_prot`-`Continue`��

#### ׼������

1. �뵰�׽ṹ���ƣ�����ĽṹҲȱ����ԭ�ӣ�������Ҫ�����ԭ�Ӳ��Ҷ�����Щ���ǿ�����ת������������docking��

2. ��PDB�ṹ����ȡ�����ԭ��λ�á�`indinavir`������л�����Ϊ`MK1`����`HETATM`��ͷ���б�ʾ��ԭ�� (heteroatoms)��

  * Linuxϵͳ�£�����`grep "^HETATM.*MK1" 1hsg.pdb >indinavir.pdb`
  * Windowsϵͳ�£�ֱ�ӿ���

3. ���ṹ����ADT��`File`-`Read Molecule`-`indinavir.pdb`;`Color`-`By Atom Type`-`All Geometreies`-`OK`��

4. ����ṹ��ͨ��ȱ����ԭ�� (��Ϊ��ԭ�ӵ����٣������Ӻ˶Ե�����������������˺��Ѷ�λ�������<http://www.uh.edu/~chembi/ChemSocRev_Jones_critical.pdf>)��������docking�����У���ԭ�ӣ������Ǽ�����ԭ�ӶԼ��㾲�������Ǳ���ġ����������Ҫ�����������ԭ�ӣ�`Edit`-`Hydrogen`-`Add`-`Polar only`-`OK`(֮����ѡ��`Polar only`����Ϊ`vina`�Ĺٷ���Ƶ��������ôѡ���)����ʱ��ԭ�ӻ��԰�ɫ������ʽ���֡�

<figure class="half">
	<img src="{{ site.imgurl }}/docking/indinavir_no_H.png" alt="1hsg_prot_no_H.png">
	<img src="{{ site.imgurl }}/docking/indinavir_with_H.png" alt="1hsg_prot_with_H.png">
	<figcaption>������ԭ��ǰ���󣩺ͺ��ң�������ṹ��ʾ</figcaption>
</figure>

5. ��ADT�ж���˻�����Ϊ���壬�Ա�ADTΪ�����ֲ����(partial charges)�����ÿ���ת�������`Ligand`-`input`-`Choose`-`indinavir`-`Select Molecule for AutoDock4`����ʱ����һ��������ָʾADT�����Ĳ����������ϲ��Ǽ����⣨ֻ������˵�����£��������ɵ�����������ת����Ȼ��洢���`Ligand`-`Output`-`Save as PDBQT`��

  * `indinavir.pdbqt`Ϊֻ���˼�����Ľ��
  * `indinavir_all_h.pdbqt`Ϊ����������Ľ��

�鿴ADT��������ת����`Ligand`-`Torsion Tree`-`Choose Torsions`,���Կ���`Number of rotatable bonds=14/32`��

��������pdbqt���⣬`Lignad`-`Output`-`Dave as PDBQT`

#### ׼��docking�����ļ�

docking�����ļ���������������壨���ף������壨�������������������Ϣ��Ϊһ���ı��ļ����������⣬����Ϊ`conf.txt`����������

```
receptor = 1hsg_prot.pdbqt
ligand   = indinavir.pdbqt

num_modes = 50

out = dockingResult.pdbqt
log = docking.log

center_x = 16
center_y = 25
center_z = 4

size_x = 30
size_y = 30
size_z = 30

seed = 2009
```

### Docking indinavir��HIV-1����ø

1. ʹ��[`AutoDock Vina`](http://vina.scripps.edu/)ִ��dockingԤ�⡣

2. ��windows��������ʾ����linux�ն����������� `vina --config conf.txt`�����м����ӡ�

3. ���е�������������ļ�������ļ�`dockingResult.pdbqt`����־�ļ�`docking.log`��
  * `dockingResult.pdbqt`: ��������docking��ģʽ����һ��Ϊ�����õĹ���
  * `docking.log`: ��־�ļ��������������ֵ����һ�У�Խ��Խ�ȶ�����һ��Ϊ��õĹ��󣩡�ÿ���������һ������ľ��롢ÿ���������һ������Ĳ��
    
	```
    Detected 4 CPUs
    Reading input ... done.
    Setting up the scoring function ... done.
    Analyzing the binding site ... done.
    Using random seed: 2009
    Performing search ... done.
    Refining results ... done.
    
    mode |   affinity | dist from best mode
         | (kcal/mol) | rmsd l.b.| rmsd u.b.
    -----+------------+----------+----------
       1        -11.5      0.000      0.000
       2        -10.6      1.425      4.304
       3        -10.4      2.042     10.990
       4        -10.3      2.034     10.326
	```

4. ��`PyMOL`���ӻ�docking���

`File`-`Open`�ļ�����ѡ��`All FIles`-ѡȡ���`pdbqt�ļ�`��`ԭʼ���׺������pdb�ļ�`��`ԭ�̵̳�pdbqt�ļ�`��
  
  * dockingResult.pdbqt: ���ӷǼ������docking���
  * dockingResultAllH.pdbqt: �����������docking���
  * original_tutorial_result.pdbqt��ԭ�̳��е�docking���

<figure class="third">
	<img src="{{ site.imgurl }}/docking/docking_result_all.png" alt="docking_result_all.png">
	<img src="{{ site.imgurl }}/docking/our_ligand_gold_standard.png" alt="our_ligand_gold_standard.png">
	<img src="{{ site.imgurl }}/docking/our_ligand_original_ligand.png" alt="our_ligand_original_ligand.png">
	<figcaption>Docking���չʾ����ɫ������ΪԭPDB����ṹ������Ĺ�����Ϊ���׼����ɫΪ���̵̳Ľ��ֻ�Ӽ����⡣�ۺ�ɫΪԭ�̳̽������ɫΪ���̳̼�������Ľ�� (����ɫ������ȫһ�£������ʾ����)��</figcaption>
</figure>

### Docking��ԭ������

��ǰ��������У�`AutoDock Vina`�ܰ�����dock������ԭ���Ĺ������棬���ǳ�������һ������ҩ��[`nelfinavir�η���Τ`](http://en.wikipedia.org/wiki/Nelfinavir)����չʾ���Ѱ��С�����ڵ����ڵĽ��λ�㡣������̿��Խ�һ������������չ����Ϊ������ɸѡ(virtual screening)���Ĳ��衣

* ����վ<https://pubchem.ncbi.nlm.nih.gov/compound/64143#section=3D-Conformer>�����3D��������`SDF`��ʽ���ļ���

* ����վ<http://www.drugbank.ca/drugs/DB00220>���`PDB`��ʽ���ļ���
  * DB00220_nelfinavir.pdb��Ϊ�����ص�pdb�ļ�,��һ��ƽ��PDB�ṹ��
  * nelfinavir.pdb��Ϊ�̳��ṩ��pdb�ļ�

* ������������������ļ�����Ԥ������`pdbqt`��ʽ�ļ���

* �޸������ļ���ִ��Docking��

* ��`pymol`���ӻ������

* ���������������PDB�д���nelfinavir��HIV-1����ø�ľ���ṹ([1OHR](http://www.rcsb.org/pdb/explore/explore.do?structureId=1OHR))��������Ϊ���׼�����docking��׼ȷ�ԡ�

* pymol�е���`1OHR.pdb`�ļ����ڶ�������`1OHR`�У����`H`-`hide everything`�����`S`-`show cartoons`��`C`-`By chain`����ͼ�п��Կ�������������ø���ڿռ�ķ���ͬ�����������Ҫ���±ȶ��������ṹ,`PyMOL> align 1OHR, 1hsg_prot`�����Կ��������ṹ��ȫ�غ��ˡ�

You may have observed that moving the structure around the window is a bit difficult since the origin of the view has been altered when you loaded 1OHR.pdb. To reset it, try:`PyMOL> reset`������֮��û�п����仯��

��ȡ`1OHR`�е�`nelfinavir (�л�Ϊ1UN)`,`PyMOL> select nelfinavir, 1OHR and resn 1UN`��������������չʾ��ʽ��`S`-`sticks`, `C`-`white`��

<figure class="half">
	<img src="{{ site.imgurl }}/docking/1OHR_1HSG_unalign.png" alt="1OHR_1HSG_unalign.png">
	<img src="{{ site.imgurl }}/docking/1OHR_1HSG_align.png" alt="1OHR_1HSG_align.png">
	<figcaption>Docking���չʾ����һ��ͼ��ʾ2������ṹalignǰ��չʾ���ڶ���ͼ��ʾ2������align���غ�����һ�𡣰�ɫ������Ϊ1OHR PDB����ṹ������nelfinavir�Ĺ�����Ϊ���׼����ɫΪ���̵̳Ľ��(ֻ�Ӽ�����)��</figcaption>
</figure>

ͨ������׼�ȶԣ��ж��ĸ�������Ԥ������ģʽ��

<figure class="half">
	<img src="{{ site.imgurl }}/docking/nelfinavir_first_with_gold_standard.png" alt="nelfinavir_first_with_gold_standard.png">
	<img src="{{ site.imgurl }}/docking/nelfinavir_second_with_gold_standard.png" alt="nelfinavir_second_with_gold_standard.png">
	<figcaption>Docking��һ��ͼ��ʾAutoDock Vina��������Best Mode����׼�ıȶ�������ڶ���ͼ��ʾAutoDock Vina��������Second Best Mode����׼�ıȶ��������ɫ������Ϊ1OHR PDB����ṹ������nelfinavir�Ĺ�����Ϊ���׼����ɫΪ���̵̳Ľ��(ֻ�Ӽ�����)��</figcaption>
</figure>

�������`second best mode`����ȥ�Ǻϵĸ��ã�Ϊʲô�أ�����־�Ľ������������`best mode`��`second best mode`ֻ����0.2��

��ô����һ�����⣬1SHG��chainA��1OHR��chainA�ǲ���һ���أ����Ǳȶ�1OHR��chainA��1HSG��chainB��`PyMOL> align 1OHR and chain A, 1hsg_prot and chain B`��

<figure class="half">
	<img src="{{ site.imgurl }}/docking/1OHR_1HSG_chainA_align.png" alt="1OHR_1HSG_chainA_align.png">
	<img src="{{ site.imgurl }}/docking/1OHR_1HSG_chainAB_align.png" alt="1OHR_1HSG_chainAB_align.png">
	<figcaption>Docking���չʾ����һ��ͼ��ʾ2������ṹalign���غ�����һ�𡣵ڶ���ͼ��ʾ1OHR��chainA��1HSG��chainB�ȶԵĽ������ɫ������Ϊ1OHR PDB����ṹ������nelfinavir�Ĺ�����Ϊ���׼����ɫΪ���̵̳�Ԥ���second best mode���(ֻ�Ӽ�����)��</figcaption>
</figure>

### �ڵ��ױ��������� (electrostatic surface)

���������ڷ���docking�����з�������Ҫ�����á����ǽ��������۲쾲������������������õġ�

ǰ�������ᵽ��PDB�ṹ�в�����ԭ�ӵľֲ������Ϣ������Ծ��������ļ����Ǻ���Ҫ�ġ����������Ҫ��PDB�ļ���������һ���ݡ�





### �ο�

* Detailed tutorial <http://sbcb.bioch.ox.ac.uk/users/greg/teaching/docking-2012.html>
* �ٷ��ĵ� <http://vina.scripps.edu>
* PyMOL�����ֲ� <https://pymolwiki.org/index.php/Practical_Pymol_for_Beginners>
