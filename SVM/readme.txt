֧���������㷨


SMO�㷨�ܹ�ͨ����������㲻�ϵض�alphas��b���е�����ֱ�����������ֵ
SMO�㷨�Ĳ������£�
* ����1��������
	fx = wx + b����fx��ֵ
	�������ճ��ӷ��Ż����Եó�w��ֵΪ(1~n)��i alphai*yi*xi
	i����Ei  = fXi - labelMat[i]
	j����Ej  = fXj - labelMat[j]

* ����2���������½�L��H��
	���labelI != labelJ
		L = max(0, alphaJold - alphaIold)
        	H = min(C, C + alphaJold - alphaIold)
	���labelI == labelJ
		L = max(0, alphaJold + alphaIold - C)
		H = min(C, alphaJold + alphaIold)

* ����3������ǣ�
	�� = 2 * xi * xj.T - xi * xi.T - xj * xj.T 

* ����4�����¦�j�� 
	alphaJnew = alphaJold - yj(Ei - Ej) / ��
	
* ����5������ȡֵ��Χ�޼���j��
	if aj > H:
        	alphaJnewClipped = H
    	if aj < L:
        	alphaJnewClipped = L
	else:
		alphaJnewClipped = alphaJnew

* ����6�����¦�i�� 
	alphaInew = alphaIold + yi*yj*(alphaJold - alphaJnewClipped)

* ����7������b1��b2�� 
	b1New = bOld - Ei - yj * (alphaInew - alphaIold) * xi.T * xi - yj * (alphaJnew - alphaJold) * xj.T *xi
	b2New = bOld - Ej - yi * (alphaInew - alphaIold) * xi.T * xj - yj * (alphaJnew - alphaJold) * xj.T *xj

* ����8������b1��b2����b�� 
	if (0 < alphas[i] and alphas[i] < C):
        	b = b1
        elif (0 < alphas[j] and alphas[j] < C):
                b = b2
        else:
                b = (b1 + b2) / 2.0

