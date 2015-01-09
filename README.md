# docker-orthanc
Docker for [Orthanc](http://www.orthanc-server.com/) a DICOM server for medical imaging.

## Build
##### Build orthanc image

    sudo docker build  --rm -t <username>/orthanc git://github.com/logocomune/docker-orthanc.git

##### Build Data in Container (Optional)

    sudo docker run -t --name orthanc_data -v /var/lib/orthanc/db-v5 busybox echo "done"

### Run
##### Run with orthanc.json configuration

    sudo docker run  -d --rm  -p 4242:4242 -p 8042:8042  \
      --volumes-from orthanc_data  \
      <username>/orthanc
      
##### Run with custom configuration

    sudo docker run  -d --rm  -p 4242:4242 -p 8042:8042  \
      --volumes-from orthanc_data  \
      -v /my/path/my_orthanc_configuration.json:/etc/orthanc/orthanc.json:ro \
      <username>/orthanc



