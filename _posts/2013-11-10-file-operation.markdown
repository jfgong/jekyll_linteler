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
	FILE* fp_out = fopen(file.in,"r");
	FILE* fp_in = fopen(file.in,"w");

	/*
	 * When last line is "\n" in file, distinguish:
	 * "!feof(fp)" and "NULL != fgets(str,len,fp)"
	 * For last line, former will execute loop but latter will not
	 */
	while (!feof(fp_in)) {
	    // fgets will read '\n' into str if LENGTH long enough
	    fgets(str, LENGTH + 1, fp_in);
	    fputs(str, fp_out);
	}


#问题


Posted by randombug @ {{ page.date | date_to_string }}
