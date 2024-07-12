---
title: Trick
data: 2024-7-9 19:52:54
updated: 2024-7-9
tags: 
    - TA
    - Technology
categories: Technology
description: trick
cover: https://yin-qin.oss-cn-shanghai.aliyuncs.com/XiaoYao/202403191721929.jpg
---

# 范围检测

```
using UnityEngine;
 
public class RangeCheck
{
    //--扇形
    public static bool CurveRange(Transform self, Transform target, float maxDistance, float maxAngle)
    {
        return CurveRange(self, target, 0, maxDistance, maxAngle);
    }
    public static bool CurveRange(Transform self, Transform target, float minDistance, float maxDistance, float maxAngle)
    {
        Vector3 playerDir = self.forward;
        Vector3 enemydir = (target.position - self.position).normalized;
        float angle = Vector3.Angle(playerDir, enemydir);
        if (angle > maxAngle * 0.5f)
        {
            return false;
        }
        float distance = Vector3.Distance(target.position, self.position);
        if (distance <= maxDistance && distance >= minDistance)
        {
            return true;
        }
        return false;
    }
    //--圆形
    public static bool CircleRange(Transform self, Transform target, float maxDistance)
    {
        return CircleRange(self, target, 0, maxDistance);
    }
    public static bool CircleRange(Transform self, Transform target, float minDistance, float maxDistance)
    {
        float distance = Vector3.Distance(target.position, self.position);
        if (distance <= maxDistance && distance >= minDistance)
        {
            return true;
        }
        else
        {
            return false;
        }
    }
    //--矩形
    public static bool SquareRange(Transform self, Transform target, float maxWidth, float maxHeight)
    {
        return SquareRange(self, target, maxWidth, 0, maxHeight);
    }
    public static bool SquareRange(Transform self, Transform target, float maxWidth, float minHeight, float maxHeight)
    {
        Vector3 enemyDir = (target.position - self.position).normalized;
        float angle = Vector3.Angle(enemyDir, self.forward);
        if (angle > 90)
        {
            return false;
        }
        float distance = Vector3.Distance(target.position, self.position);
        float z = distance * Mathf.Cos(angle * Mathf.Deg2Rad);
        float x = distance * Mathf.Sin(angle * Mathf.Deg2Rad);
        if (x <= maxWidth * 0.5f && z <= maxHeight && z >= minHeight)
        {
            return true;
        }
        return false;
    }
    //--等腰三角形
    public static bool TriangleRange(Transform self, Transform target, float maxDistance, float maxAngle)
    {
        Vector3 playerDir = self.forward;
        Vector3 enemydir = (target.position - self.position).normalized;
        float angle = Vector3.Angle(playerDir, enemydir);
        if (angle > maxAngle * 0.5f)
        {
            return false;
        }
        float angleDistance = maxDistance * Mathf.Cos(maxAngle * 0.5f * Mathf.Deg2Rad) / Mathf.Cos(angle * Mathf.Deg2Rad);
        float distance = Vector3.Distance(target.position, self.position);
        if (distance <= angleDistance)
        {
            return true;
        }
        return false;
    }
}
```

# 视锥体剔除

```

public class MyCull : MonoBehaviour
{
    private Camera _camera;
    public Transform parentTrans;
    private Renderer[] meshRenders;
 
 
    void Start()
    {
        _camera = GetComponent<Camera>();
        meshRenders = parentTrans.GetComponentsInChildren<MeshRenderer>();
    }
 
    // Update is called once per frame
    void Update()
    {
		Plane[] cameraPlane = GeometryUtility.CalculateFrustumPlanes(_camera);//得到摄像机的视锥平面
        foreach (var item in meshRenders)
        {
            Bounds bounds = item.bounds;
            bool isShow = GeometryUtility.TestPlanesAABB(cameraPlane,bounds);//判断是否在摄像机的视锥体中
            item.enabled = isShow;
        }
    }
}
```

