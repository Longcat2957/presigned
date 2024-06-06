# S3 File Upload/Download Example

이 프로젝트는 Python과 boto3 라이브러리를 사용하여 Amazon S3에 파일을 업로드하고 다운로드하는 예제입니다. 프로젝트에는 `s3Handler` 클래스와 `FileHandler` 클래스가 포함되어 있습니다.

## 전제 조건

- Python 3.x 버전이 설치되어 있어야 합니다.
- `boto3`와 `requests` 라이브러리가 설치되어 있어야 합니다. 다음 명령어를 사용하여 설치할 수 있습니다:
  ```
  pip install boto3 requests
  ```
- AWS 액세스 키와 시크릿 키가 필요합니다. IAM 사용자를 생성하고 해당 사용자에게 필요한 S3 권한을 부여해야 합니다.

## 설정

1. `config` 딕셔너리에 AWS 액세스 키, 시크릿 키, 버킷 이름 등의 설정 정보를 입력합니다.

```python
config = {
    'aws_access_key_id': 'YOUR_ACCESS_KEY',
    'aws_secret_access_key': 'YOUR_SECRET_KEY',
    'bucket_name': 'YOUR_BUCKET_NAME',
    'region_name': 'YOUR_REGION_NAME'
}
```

2. `s3Handler` 클래스의 `__init__` 메서드에서 `root_dir`을 설정합니다. 이 디렉토리는 S3 버킷 내에서 파일이 저장될 루트 디렉토리입니다.

```python
self.root_dir = 'test'  # S3 버킷 내의 루트 디렉토리 이름
```

3. `FileHandler` 클래스의 `__init__` 메서드에서 `upload_files_dir`과 `download_files_dir`을 설정합니다. 이 디렉토리는 로컬 시스템에서 업로드할 파일과 다운로드한 파일이 저장될 디렉토리입니다.

```python
self.upload_files_dir = "./upload"  # 업로드 파일 디렉토리 경로
self.download_files_dir = "./download"  # 다운로드 파일 디렉토리 경로
```

## 사용 방법

1. 업로드할 파일을 `upload_files_dir`에 지정된 디렉토리에 저장합니다.

2. `FileHandler` 클래스의 인스턴스를 생성합니다.

```python
file_handler = FileHandler(handler)
```

3. `single_file_upload` 메서드를 호출하여 파일을 업로드합니다. 파일의 절대 경로를 인자로 전달합니다.

```python
file_handler.single_file_upload("./upload/test.txt")
```

4. `single_file_download` 메서드를 호출하여 파일을 다운로드합니다. 다운로드할 파일의 이름을 인자로 전달합니다.

```python
file_handler.single_file_download("test.txt")
```

5. 다운로드한 파일은 `download_files_dir`에 지정된 디렉토리에 저장됩니다.
