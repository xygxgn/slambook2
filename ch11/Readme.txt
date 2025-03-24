报错:
 没有规则可制作目标“/usr/local/lib/libDBoW3.a”，由“loop_closure” 需求。
解决方案
在 CMakeLists.txt 中
修改
set( DBoW3_LIBS "/usr/local/lib/libDBoW3.a" )
为
set( DBoW3_LIBS "/usr/local/lib/libDBoW3.so" )


问题:


解决方案
下载数据集
https://vision.in.tum.de/data/datasets/rgbd-dataset/download
选择 fr1/desk2 下载，并解压到工作目录下
将数据集 rgb.txt 的注释部分删去，即删去
# color images
# file: 'rgbd_dataset_freiburg1_desk2.bag'
# timestamp filename
将数据集 depth.txt 的注释部分删去，即删去
# depth maps
# file: 'rgbd_dataset_freiburg1_desk2.bag'
# timestamp filename

在 gen_vocab_large.cpp 中
    string dataset_dir = argv[1];
    ifstream fin ( dataset_dir+"/associate.txt" );
    if ( !fin )
    {
        cout<<"please generate the associate file called associate.txt!"<<endl;
        return 1;
    }
    
    while ( !fin.eof() )
    {
        string rgb_time, rgb_file, depth_time, depth_file;
        fin>>rgb_time>>rgb_file>>depth_time>>depth_file;
        rgb_times.push_back ( atof ( rgb_time.c_str() ) );
        depth_times.push_back ( atof ( depth_time.c_str() ) );
        rgb_files.push_back ( dataset_dir+"/"+rgb_file );
        depth_files.push_back ( dataset_dir+"/"+depth_file );

        if ( fin.good() == false )
            break;
    }
    fin.close();
替换为
    string dataset_dir = argv[1];
    ifstream fin_rgb ( dataset_dir+"/rgb.txt" );
    if ( !fin_rgb )
    {
        cout<<"please generate the associate file called rgb.txt!"<<endl;
        return 1;
    }
    ifstream fin_depth ( dataset_dir+"/depth.txt" );
    if ( !fin_depth )
    {
        cout<<"please generate the associate file called depth.txt!"<<endl;
        return 1;
    }

    vector<string> rgb_files, depth_files;
    vector<double> rgb_times, depth_times;
    while ( !fin_rgb.eof() && !fin_depth.eof())
    {
        string rgb_time, rgb_file, depth_time, depth_file;
        fin_rgb>>rgb_time>>rgb_file;
        fin_depth>>depth_time>>depth_file;
        rgb_times.push_back ( atof ( rgb_time.c_str() ) );
        depth_times.push_back ( atof ( depth_time.c_str() ) );
        rgb_files.push_back ( dataset_dir+"/"+rgb_file );
        depth_files.push_back ( dataset_dir+"/"+depth_file );
        
        if ( fin_rgb.good() == false || fin_depth.good() == false )
            break;
    }
    fin_rgb.close();
    fin_depth.close();
重新编译，并在终端运行
build/gen_vocab rgbd_dataset_freiburg1_desk2