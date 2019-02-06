#!/bin/sh
# Generates a file with random binary contents

echo "Running random file generator"

display_help()
{
	echo -e "\n---Random file generator---"
	echo "  Usage:"
	echo "    [script_name] [num files] [file size]"
	echo "    Example run that creates 3 files at 10 MB each:"
	echo "    ./file_gen.sh 3 10"
}

# Get the file count; default=1
file_count=${1}
if [ -z $file_count ]; then
	echo "Using default file count of 1 file"
        file_count=1
elif [ $file_count -lt 1 ]; then
	echo "File count cannot be less than 1"
	display_help
	exit 1
fi
echo "Generating ${file_count} file(s)"

# Get the file size; default=10MB
file_size=${2}
if [ -z $file_size ]; then
	echo "Using default file size of 10MB"
        file_size=10
elif [ $file_size -lt 1 ]; then
	echo "File size cannot be less than 1"
	display_help
	exit 1
fi
echo "File size set to ${file_size} MB"

count=0
while [ $count -lt $file_count ]; do

	# File size, ex: 10M
        file_size_MB="${file_size}M"

	# Datetime, ex: 20190201_172628234796411
        datetime=$(date +"%Y%m%d_%H%M%S%N")

	# File name, ex: GEN_FILE_10M_20190201_172702790450480
        file_name="GEN_FILE_${file_size_MB}_${datetime}"

	# Generate the file with random data
        head -c ${file_size_MB} </dev/urandom >${file_name}
	echo "Generated file ${file_name}"

	# Sleep so we don't go sanic fast and name files the same thing
	sleep 0.05

	#Increment
        count=$((count + 1))
done

