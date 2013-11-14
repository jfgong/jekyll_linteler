---
layout: post 
title: 文件操作
---

文件操作是编程中经常面临的问题,示例代码权当备忘,不求严谨,仅注重流程

#opendir -> readdir -> closedir#
	DIR* dirptr = opendir("*");
	struct dirent* entry;
	while (entry = readdir(dirptr)) {
	    //entry->d_type, help to judge file type(-,d)
	    FILE* fp = fopen(entry->d_name,"r");
	    fclose(fp);
	}
	closedir(dirptr);

#fgets, fputs#
	char str[STRING_SIZE];
	/*
	 * When last line is "\n" in file, distinguish:
	 * "!feof(fp)" and "NULL != fgets(str,len,fp)"
	 * For last line, former will execute loop but latter will not
	 */
	while (!feof(fp_r)) {
	    // fgets will read '\n' into str if LENGTH long enough
	    fgets(str, LENGTH + 1, fp_r);
	    fputs(str, fp_w);
	}

#fread, fwrite#
	student lucy;
	student* pBuffer = &lucy;
	// fread and fwrite use for binary file
	fread(pBuffer,sizeof(student),1,fp_r);
	fwrite(pBuffer,sizeof(student),1,fp_w);

#fscanf, fprintf#
	student lucy;
	// fscanf and fprintf use for ASCII file
	fscanf(fp_r,"%d %s",&lucy.ID,lucy.address);
	fprintf(fp_w,"%d %s",lucy.ID,lucy.address);

Posted by randombug @ {{ page.date | date_to_string }}
